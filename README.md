import 'package:flutter/material.dart';

void main() {
  runApp(new MaterialApp(
    home: new Halamansatu(),
    title: "Navigasi",
    routes: <String,WidgetBuilder>{
  '/Halamansatu' : (BuildContext context) => new Halamansatu(),
  '/Halamandua' : (BuildContext context) => new Halamandua(),
}
  ));
}




class Halamansatu extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    Widget build(BuildContext context) {
    Widget imageSection = Container(
      child: Image.asset('images/ulos.jpg'),
    );
    Widget titleSection = Container(
      padding: EdgeInsets.only(top: 16),
      child: Text(
        'QUIS MOBILE',
        textAlign: TextAlign.center,
        style: TextStyle(
          fontWeight: FontWeight.bold,
          fontSize: 18,
        ),
      ),
    );

    return new Scaffold(
      appBar:new AppBar(title: new Text("Home"),),
      body: new Center(
        child:new IconButton(
          icon: new Icon(Icons.android, size : 50.0, color: Colors.green,),
          onPressed: (){
            Navigator.pushNamed(context, '/Haldua');
          },
          
        ),
      ),
     
    );
  }
}

class DataMurid{
  String nama;
  String kelas;
  String jkelamin;
  
  
  DataMahasiswa({this.nama, this.kelas, this.jkelamin});
  
}


class Halamandua extends StatefulWidget {
  _MyappState createState() => _MyappState();
}

class _MyappState extends State<Haldua> {
  
  final txtnamamurid = TextEditingController();
  final txtkelas = TextEditingController();
  final txtjkelamin = TextEditingController();
  

  List<Widget> data = [];

  onTambah() {
    setState(() {
      data.add(ListTile(
        leading: Icon(Icons.people),
        title: Text(txtnamamurid.text),
        subtitle: Text(txtjkelamin.text),
        trailing: Text(txtkelas.text),
      ));
      txtnamamurid.clear();
      txtkelas.clear();
      txtjkelamin.clear();
    });
  }

  Widget build(BuildContext context) {
    return ListView(
      children: <Widget>[
        new Container(
          padding: EdgeInsets.all(10.0),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: <Widget>[
              TextField(
                controller: txtnamamurid,
                decoration: InputDecoration(hintText: 'Nama Mahasiswa'),
              ),
              TextField(
                controller: txtkelas,
                decoration: InputDecoration(hintText: 'Jurusan'),
              ),
              TextField(
                controller: txtjkelamin,
                decoration: InputDecoration(hintText: 'Jenis Kelamin'),
              ),
              Divider(height: 5.0),
              ElevatedButton(child: Text("Tambah"), onPressed: onTambah),
            ],
          ),
        ),
        new Column(
          children: data,
        )
      ],
    );
  }
}
