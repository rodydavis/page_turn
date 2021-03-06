# page_turn_example

Demonstrates how to use the page_turn plugin.

## Screenshots

![info](https://github.com/AppleEducate/page_turn/blob/master/screenshots/demo.gif?raw=true)
![info](https://github.com/AppleEducate/page_turn/blob/master/screenshots/turn.png?raw=true)
![info](https://github.com/AppleEducate/page_turn/blob/master/screenshots/cutoff.png?raw=true)

## Example

```dart
import 'package:flutter/material.dart';

import 'package:page_turn/page_turn.dart';

import '../common/index.dart';

class HomeScreen extends StatefulWidget {
  const HomeScreen({
    Key key,
  }) : super(key: key);

  @override
  _HomeScreenState createState() => _HomeScreenState();
}

class _HomeScreenState extends State<HomeScreen> {
  final _controller = GlobalKey<PageTurnState>();
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: PageTurn(
        key: _controller,
        backgroundColor: Colors.white,
        showDragCutoff: false,
        lastPage: Container(child: Center(child: Text('Last Page!'))),
        children: <Widget>[
          for (var i = 0; i < 20; i++) AlicePage(page: i),
        ],
      ),
      floatingActionButton: FloatingActionButton(
        child: Icon(Icons.search),
        onPressed: () {
          _controller.currentState.goToPage(2);
        },
      ),
    );
  }
}

```