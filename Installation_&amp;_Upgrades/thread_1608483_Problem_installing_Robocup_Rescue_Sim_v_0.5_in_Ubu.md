---
title: "Problem installing Robocup Rescue Sim v 0.5 in Ubuntu 10.10"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by Lewke on 2010-10-29
Try to make the files (as far as i can see i have the relevant dependencies) and it throws a couple of errors that i don´t really understand.

```

make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/librescue'
g++ -g -Wall  -pipe -g -Wall  -pipe -fPIC  -c -o objects.o objects.cc
g++ -g -Wall  -pipe -g -Wall  -pipe -fPIC  -c -o error.o error.cc
error.cc: In function ‘void Librescue::dumpBytes(Librescue::LogLevel, const char*, int)’:
error.cc:98: error: ‘snprintf’ was not declared in this scope
error.cc: In function ‘void Librescue::dumpBytes(Librescue::LogLevel, const Librescue::Byte*, int)’:
error.cc:106: error: ‘snprintf’ was not declared in this scope
error.cc: In function ‘void Librescue::dumpBytes(Librescue::LogLevel, const Librescue::Bytes&)’:
error.cc:115: error: ‘snprintf’ was not declared in this scope
error.cc: In function ‘void Librescue::dumpBytes(Librescue::LogLevel, Librescue::InputBuffer&)’:
error.cc:126: error: ‘snprintf’ was not declared in this scope
make[1]: *** [error.o] Error 1
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/librescue'
blockadessimulator
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/blockadessimulator'
g++ -g -Wall  -pipe -g -Wall  -pipe -DNDEBUG -I../librescue  -c -o blockade.o blockade.cc
In file included from ../librescue/connection_manager.h:20,
                 from ../librescue/simulator.h:24,
                 from blockade.h:20,
                 from blockade.cc:18:
../librescue/udp.h: In member function ‘void Librescue::LongUDPConnection::Fragment::fill(Librescue::INT_16, Librescue::INT_16, Librescue::INT_16, Librescue::Byte*, int)’:
../librescue/udp.h:54: error: ‘memcpy’ was not declared in this scope
blockade.cc: In member function ‘virtual int BlockadeSimulator::step(Librescue::INT_32, const Librescue::AgentCommandList&, Librescue::ObjectSet&)’:
blockade.cc:63: error: ‘sort’ was not declared in this scope
blockade.cc:74: error: ‘atoi’ was not declared in this scope
make[1]: *** [blockade.o] Error 1
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/blockadessimulator'
collapsesimulator
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/collapsesimulator'
g++ -g -Wall  -pipe -g -Wall  -pipe -DNDEBUG -I../librescue  -c -o main.o main.cc
In file included from ../librescue/connection_manager.h:20,
                 from ../librescue/simulator.h:24,
                 from collapse.h:12,
                 from main.cc:7:
../librescue/udp.h: In member function ‘void Librescue::LongUDPConnection::Fragment::fill(Librescue::INT_16, Librescue::INT_16, Librescue::INT_16, Librescue::Byte*, int)’:
../librescue/udp.h:54: error: ‘memcpy’ was not declared in this scope
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/collapsesimulator'
firesimulator
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/io'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/io'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/kernel'
make[3]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/kernel/viewer'
make[4]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/kernel/viewer/monitor'
make[4]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/kernel/viewer/monitor'
make[4]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/kernel/viewer/extinguishManager'
make[4]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/kernel/viewer/extinguishManager'
make[3]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/kernel/viewer'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/kernel'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/simulator'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/simulator'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/util'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/util'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/world'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator/world'
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/firesimulator'
gis
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/gis'
g++ -g -Wall  -pipe -g -Wall  -pipe -DNDEBUG -I../librescue  -c -o main.o main.cc
In file included from ../librescue/connection_manager.h:20,
                 from main.cc:18:
../librescue/udp.h: In member function ‘void Librescue::LongUDPConnection::Fragment::fill(Librescue::INT_16, Librescue::INT_16, Librescue::INT_16, Librescue::Byte*, int)’:
../librescue/udp.h:54: error: ‘memcpy’ was not declared in this scope
main.cc: In function ‘void addNewObject(Librescue::Config&, Librescue::ObjectPool&, Librescue::RescueObject*)’:
main.cc:64: error: ‘srand’ was not declared in this scope
main.cc:69: error: ‘rand’ was not declared in this scope
main.cc: In function ‘Librescue::INT_32 readInt(FILE*)’:
main.cc:85: error: ‘exit’ was not declared in this scope
main.cc:87: error: ‘exit’ was not declared in this scope
main.cc:89: error: ‘exit’ was not declared in this scope
main.cc:91: error: ‘exit’ was not declared in this scope
main.cc: In function ‘void readRoads(Librescue::Config&, Librescue::ObjectPool&)’:
main.cc:196: error: ‘strerror’ was not declared in this scope
main.cc:197: error: ‘exit’ was not declared in this scope
main.cc: In function ‘void readNodes(Librescue::Config&, Librescue::ObjectPool&)’:
main.cc:232: error: ‘strerror’ was not declared in this scope
main.cc:233: error: ‘exit’ was not declared in this scope
main.cc: In function ‘void readBuildings(Librescue::Config&, Librescue::ObjectPool&)’:
main.cc:284: error: ‘strerror’ was not declared in this scope
main.cc:285: error: ‘exit’ was not declared in this scope
main.cc: In function ‘void readGisini(Librescue::Config&, Librescue::ObjectPool&)’:
main.cc:365: error: ‘strerror’ was not declared in this scope
main.cc:366: error: ‘exit’ was not declared in this scope
main.cc:425: error: ‘exit’ was not declared in this scope
main.cc:433: error: ‘exit’ was not declared in this scope
main.cc: In function ‘void replaceBuilding(Librescue::INT_32, Librescue::Building*, Librescue::ObjectPool&)’:
main.cc:445: error: ‘exit’ was not declared in this scope
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/gis'
kernel
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/kernel'
g++ -g -Wall  -pipe -g -Wall  -pipe -DNDEBUG -I../librescue  -c -o kernel.o kernel.cc
In file included from ../librescue/connection_manager.h:20,
                 from kernel.h:22,
                 from kernel.cc:18:
../librescue/udp.h: In member function ‘void Librescue::LongUDPConnection::Fragment::fill(Librescue::INT_16, Librescue::INT_16, Librescue::INT_16, Librescue::Byte*, int)’:
../librescue/udp.h:54: error: ‘memcpy’ was not declared in this scope
In file included from kernel.cc:20:
../librescue/handy.h: At global scope:
../librescue/handy.h:67: error: ‘clock_t’ in namespace ‘std’ does not name a type
kernel.cc: In member function ‘void Rescue::Kernel::init(int, char**)’:
kernel.cc:41: error: ‘strcmp’ was not declared in this scope
kernel.cc:92: error: ‘strlen’ was not declared in this scope
kernel.cc: In member function ‘void Rescue::Kernel::run()’:
kernel.cc:109: error: ‘memset’ was not declared in this scope
kernel.cc: In member function ‘void Rescue::Kernel::handleChannelCommand(Librescue::ChannelCommand*, Librescue::Address&)’:
kernel.cc:679: warning: comparison between signed and unsigned integer expressions
kernel.cc:690: warning: comparison between signed and unsigned integer expressions
kernel.cc: In member function ‘bool Rescue::Kernel::canHear(const Rescue::Kernel::Agent*, const Librescue::VoiceCommand*)’:
kernel.cc:984: warning: unused variable ‘hearer’
make[1]: *** [kernel.o] Error 1
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/kernel'
miscsimulator
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/miscsimulator'
g++ -g -Wall  -pipe -g -Wall  -pipe -DNDEBUG -I../librescue  -c -o main.o main.cc
In file included from ../librescue/connection_manager.h:20,
                 from ../librescue/simulator.h:24,
                 from ../librescue/container.h:22,
                 from main.cc:17:
../librescue/udp.h: In member function ‘void Librescue::LongUDPConnection::Fragment::fill(Librescue::INT_16, Librescue::INT_16, Librescue::INT_16, Librescue::Byte*, int)’:
../librescue/udp.h:54: error: ‘memcpy’ was not declared in this scope
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/miscsimulator'
civilian
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/civilian'
g++ -g -Wall  -pipe -g -Wall  -pipe -I../librescue  -c -o civilian.o civilian.cc
In file included from ../librescue/connection_manager.h:20,
                 from ../librescue/simulator.h:24,
                 from ../librescue/container.h:22,
                 from civilian.h:22,
                 from civilian.cc:17:
../librescue/udp.h: In member function ‘void Librescue::LongUDPConnection::Fragment::fill(Librescue::INT_16, Librescue::INT_16, Librescue::INT_16, Librescue::Byte*, int)’:
../librescue/udp.h:54: error: ‘memcpy’ was not declared in this scope
In file included from civilian.cc:18:
../librescue/handy.h: At global scope:
../librescue/handy.h:67: error: ‘clock_t’ in namespace ‘std’ does not name a type
make[1]: *** [civilian.o] Error 1
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/civilian'
traffic
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/traffic'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/traffic/object'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/traffic/object'
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/traffic'
viewer
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/viewer'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/viewer/object'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/viewer/object'
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/viewer'
rescuecore
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/objects'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/objects'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/commands'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/commands'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/tools'
make[3]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/tools/mapgenerator'
make[3]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/tools/mapgenerator'
make[3]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/tools/simulationrunner'
make[3]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/tools/simulationrunner'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/tools'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/debug'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/debug'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/view'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/view'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/sample'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/sample'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/log'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/log'
make[2]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/event'
make[2]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore/event'
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/rescuecore'
ticker
make[1]: Entering directory `/home/luke/Desktop/rescue-0.50.0/programs/ticker'
g++ -g -Wall  -pipe -g -Wall  -pipe   -c -o main.o main.cc
g++ -o ticker main.o  -lX11
make[1]: Leaving directory `/home/luke/Desktop/rescue-0.50.0/programs/ticker'

```

---

