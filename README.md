flutter config --enable-web
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'VITA - Your AI Companion',
      theme: ThemeData(
        brightness: Brightness.dark,
        primarySwatch: Colors.deepPurple,
        scaffoldBackgroundColor: const Color(0xFF1A1A2E),
        fontFamily: 'Inter',
        useMaterial3: true,
      ),
      home: const MainScreen(),
    );
  }
}

class MainScreen extends StatefulWidget {
  const MainScreen({super.key});

  @override
  State<MainScreen> createState() => _MainScreenState();
}

class _MainScreenState extends State<MainScreen> {
  int _selectedIndex = 0;

  static const List<Widget> _widgetOptions = <Widget>[
    HomeScreen(),
    AcademicNavigatorPage(),
    CampusConciergePage(),
    ProactiveWellnessPage(),
  ];

  void _onItemTapped(int index) {
    setState(() {
      _selectedIndex = index;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: _widgetOptions.elementAt(_selectedIndex),
      ),
      bottomNavigationBar: Container(
        decoration: BoxDecoration(
          color: const Color(0xFF2E2E4E),
          borderRadius: const BorderRadius.only(
            topLeft: Radius.circular(24),
            topRight: Radius.circular(24),
          ),
          boxShadow: [
            BoxShadow(
              color: Colors.black.withOpacity(0.2),
              spreadRadius: 2,
              blurRadius: 10,
              offset: const Offset(0, -3),
            ),
          ],
        ),
        child: ClipRRect(
          borderRadius: const BorderRadius.only(
            topLeft: Radius.circular(24),
            topRight: Radius.circular(24),
          ),
          child: BottomNavigationBar(
            items: const <BottomNavigationBarItem>[
              BottomNavigationBarItem(
                icon: Icon(Icons.home_rounded),
                label: 'Home',
              ),
              BottomNavigationBarItem(
                icon: Icon(Icons.school_rounded),
                label: 'Academics',
              ),
              BottomNavigationBarItem(
                icon: Icon(Icons.location_on_rounded),
                label: 'Campus',
              ),
              BottomNavigationBarItem(
                icon: Icon(Icons.favorite_rounded),
                label: 'Wellness',
              ),
            ],
            currentIndex: _selectedIndex,
            selectedItemColor: Colors.deepPurpleAccent,
            unselectedItemColor: Colors.grey,
            onTap: _onItemTapped,
            backgroundColor: const Color(0xFF2E2E4E),
            type: BottomNavigationBarType.fixed,
            selectedFontSize: 12,
            unselectedFontSize: 12,
          ),
        ),
      ),
    );
  }
}

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Container(
      decoration: const BoxDecoration(
        gradient: LinearGradient(
          colors: [
            Color(0xFF1A1A2E),
            Color(0xFF2C0F4A),
          ],
          begin: Alignment.topCenter,
          end: Alignment.bottomCenter,
        ),
      ),
      child: Padding(
        padding: const EdgeInsets.symmetric(horizontal: 24.0),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            const Spacer(flex: 2),
            // App Logo/Icon
            Container(
              padding: const EdgeInsets.all(24),
              decoration: BoxDecoration(
                gradient: const RadialGradient(
                  colors: [
                    Color(0xFF9B59B6),
                    Color(0xFF6C3483),
                  ],
                  stops: [0.3, 1.0],
                ),
                shape: BoxShape.circle,
                boxShadow: [
                  BoxShadow(
                    color: Colors.deepPurpleAccent.withOpacity(0.4),
                    blurRadius: 25,
                    spreadRadius: 2,
                    offset: const Offset(0, 5),
                  ),
                ],
              ),
              child: const Icon(
                Icons.psychology_rounded,
                size: 80,
                color: Colors.white,
              ),
            ),
            const SizedBox(height: 32),
            // Title
            ShaderMask(
              shaderCallback: (Rect bounds) {
                return const LinearGradient(
                  colors: [Color(0xFFB8C0FF), Color(0xFFE0B0FF)],
                  begin: Alignment.topLeft,
                  end: Alignment.bottomRight,
                ).createShader(bounds);
              },
              child: const Text(
                'Hi, I\'m VITA',
                style: TextStyle(
                  fontSize: 48,
                  fontWeight: FontWeight.bold,
                  color: Colors.white,
                ),
                textAlign: TextAlign.center,
              ),
            ),
            const SizedBox(height: 8),
            // Subtitle
            const Text(
              'Your AI-powered campus companion.',
              style: TextStyle(
                fontSize: 16,
                color: Color(0xFFC0C0C0),
              ),
              textAlign: TextAlign.center,
            ),
            const Spacer(flex: 1),
            // Chat Input
            Container(
              padding: const EdgeInsets.all(8.0),
              decoration: BoxDecoration(
                color: const Color(0xFF2E2E4E),
                borderRadius: BorderRadius.circular(30),
                border: Border.all(color: Colors.deepPurpleAccent.withOpacity(0.5)),
                boxShadow: [
                  BoxShadow(
                    color: Colors.black.withOpacity(0.2),
                    blurRadius: 10,
                    offset: const Offset(0, 4),
                  ),
                ],
              ),
              child: Row(
                children: [
                  const SizedBox(width: 12),
                  const Expanded(
                    child: TextField(
                      style: TextStyle(color: Colors.white),
                      decoration: InputDecoration(
                        hintText: 'Ask me anything...',
                        hintStyle: TextStyle(color: Colors.grey),
                        border: InputBorder.none,
                      ),
                    ),
                  ),
                  const SizedBox(width: 8),
                  Container(
                    decoration: BoxDecoration(
                      gradient: const LinearGradient(
                        colors: [Color(0xFF9B59B6), Color(0xFF6C3483)],
                        begin: Alignment.topLeft,
                        end: Alignment.bottomRight,
                      ),
                      borderRadius: BorderRadius.circular(24),
                      boxShadow: [
                        BoxShadow(
                          color: Colors.deepPurple.withOpacity(0.6),
                          blurRadius: 10,
                          offset: const Offset(0, 4),
                        ),
                      ],
                    ),
                    child: IconButton(
                      icon: const Icon(Icons.send_rounded, color: Colors.white),
                      onPressed: () {
                        // Handle send action
                      },
                    ),
                  ),
                ],
              ),
            ),
            const Spacer(flex: 1),
          ],
        ),
      ),
    );
  }
}

class AcademicNavigatorPage extends StatelessWidget {
  const AcademicNavigatorPage({super.key});

  @override
  Widget build(BuildContext context) {
    return const Center(
      child: Text('Academic Navigator Content', style: TextStyle(fontSize: 24, color: Colors.white)),
    );
  }
}

class CampusConciergePage extends StatelessWidget {
  const CampusConciergePage({super.key});

  @override
  Widget build(BuildContext context) {
    return const Center(
      child: Text('Campus Concierge Content', style: TextStyle(fontSize: 24, color: Colors.white)),
    );
  }
}

class ProactiveWellnessPage extends StatelessWidget {
  const ProactiveWellnessPage({super.key});

  @override
  Widget build(BuildContext context) {
    return const Center(
      child: Text('Proactive Wellness Content', style: TextStyle(fontSize: 24, color: Colors.white)),
    );
  }
}


