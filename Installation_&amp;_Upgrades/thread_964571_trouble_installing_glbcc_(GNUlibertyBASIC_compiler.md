---
title: "trouble installing glbcc (GNU/libertyBASIC compiler) in 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by duanedesign on 2008-10-31
I am having trouble installing GNU/Liberty Basic Compiler Collection (GLBCC) on Intrepid Ibex. It gets almost all the way through then there is an error. 
GLBCC site: [http://lbpp.sourceforge.net/](http://lbpp.sourceforge.net/)

Here is the terminal output:

duanedesign@duanedesign-laptop:/glbcc-0.1.0$ sudo make install
[sudo] password for duanedesign: 
install -d /usr/local/lib/glbcc-lib/0.0.7/lib
install -d /usr/local/lib/glbcc-lib/0.0.7/include
make -C lbpp
make[1]: Entering directory `/glbcc-0.1.0/lbpp'
make -C src
make[2]: Entering directory `/glbcc-0.1.0/lbpp/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/glbcc-0.1.0/lbpp/src'
make[1]: Leaving directory `/glbcc-0.1.0/lbpp'
install -m555 lbpp/src/lbpp /usr/local/bin
make -C libLB clean all
make[1]: Entering directory `/glbcc-0.1.0/libLB'
make -C src clean
make[2]: Entering directory `/glbcc-0.1.0/libLB/src'
rm -f ../lib/libLB.a ../lib/lbcrt0.o ../lib/lbcrt0.xo \
              statements.o functions.o devices.o strings.o debug.o lb.o statements.xo functions.xo devices.xo strings.xo debug.xo lb.xo
make -C gui clean
make[3]: Entering directory `/glbcc-0.1.0/libLB/src/gui'
make -C gtk clean
make[4]: Entering directory `/glbcc-0.1.0/libLB/src/gui/gtk'
rm -f ../libGUI.a basic_gui.o window.o text_window.o
make[4]: Leaving directory `/glbcc-0.1.0/libLB/src/gui/gtk'
make -C Win32 clean
make[4]: Entering directory `/glbcc-0.1.0/libLB/src/gui/Win32'
rm -f ../libGUI.a basic_gui.xo
make[4]: Leaving directory `/glbcc-0.1.0/libLB/src/gui/Win32'
make[3]: Leaving directory `/glbcc-0.1.0/libLB/src/gui'
make -C stdio clean
make[3]: Entering directory `/glbcc-0.1.0/libLB/src/stdio'
rm -f libIO.a basic_io.o basic_io.xo
make[3]: Leaving directory `/glbcc-0.1.0/libLB/src/stdio'
make[2]: Leaving directory `/glbcc-0.1.0/libLB/src'
make -C src
make[2]: Entering directory `/glbcc-0.1.0/libLB/src'
make -C gui
make[3]: Entering directory `/glbcc-0.1.0/libLB/src/gui'
make -C gtk
make[4]: Entering directory `/glbcc-0.1.0/libLB/src/gui/gtk'
gcc -Wall -g `gnome-config --cflags gnome` -I../../../include   -c -o basic_gui.o basic_gui.c
gcc -c -Wall -g `gnome-config --cflags gnome` -I../../../include  -o window.o window.c
gcc -c -Wall -g `gnome-config --cflags gnome` -I../../../include  -o text_window.o text_window.c
rm -f ../libGUI.a
ar cq ../libGUI.a basic_gui.o window.o text_window.o
make[4]: Leaving directory `/glbcc-0.1.0/libLB/src/gui/gtk'
make[3]: Leaving directory `/glbcc-0.1.0/libLB/src/gui'
make -C stdio
make[3]: Entering directory `/glbcc-0.1.0/libLB/src/stdio'
gcc -c -Wall -g `gnome-config --cflags gnomeui` -I../../include  -o basic_io.o basic_io.c
rm -f libIO.a
ar cq libIO.a basic_io.o
make[3]: Leaving directory `/glbcc-0.1.0/libLB/src/stdio'
gcc -c -Wall -g `gnome-config --cflags gnomeui` -I../include  -o statements.o statements.c
gcc -c -Wall -g `gnome-config --cflags gnomeui` -I../include  -o functions.o functions.c
gcc -c -Wall -g `gnome-config --cflags gnomeui` -I../include  -o devices.o devices.c
gcc -c -Wall -g `gnome-config --cflags gnomeui` -I../include  -o strings.o strings.c
gcc -c -Wall -g `gnome-config --cflags gnomeui` -I../include  -o debug.o debug.c
gcc -c -Wall -g `gnome-config --cflags gnomeui` -I../include  -o lb.o lb.c
rm -f lib/*.o lib/*.xo
cp -f statements.o functions.o devices.o strings.o debug.o lb.o lib
cd lib; \
	 ar x ../gui/libGUI.a; \
	 ar x ../stdio/libIO.a; \
         rm -f libLB.a; \
	 ar cq libLB.a *.o; \
	 ranlib libLB.a; \
	 mv -f libLB.a ../../lib; \
	 rm -f *.o *.xo *.a
gcc -c -Wall -g `gnome-config --cflags gnomeui` -I../include  -o lbcrt0.o lbcrt0.c
mv lbcrt0.o ../lib
make[2]: Leaving directory `/glbcc-0.1.0/libLB/src'
make[1]: Leaving directory `/glbcc-0.1.0/libLB'
install -m444 libLB/lib/libLB.a /usr/local/lib/glbcc-lib/0.0.7/lib
install -m444 libLB/lib/lbcrt0.o /usr/local/lib/glbcc-lib/0.0.7/lib
for i in libLB/include/*; \
	    do install -m444 $i	 /usr/local/lib/glbcc-lib/0.0.7/include; \
	done
install: omitting directory `libLB/include/CVS'
rm -f /usr/local/lib/glbcc-lib/0.0.7/specs
echo "/usr/local/bin/lbpp -I/usr/local/lib/glbcc-lib/0.0.7/include" >> /usr/local/lib/glbcc-lib/0.0.7/specs
echo "gcc" >> /usr/local/lib/glbcc-lib/0.0.7/specs
echo "-g -I/usr/local/lib/glbcc-lib/0.0.7/include \`gnome-config --cflags gnomeui\`" \
	     >> /usr/local/lib/glbcc-lib/0.0.7/specs
echo "-L/usr/local/lib/glbcc-lib/0.0.7/lib -lLB -lm \`gnome-config --libs gnomeui\`" \
	     >> /usr/local/lib/glbcc-lib/0.0.7/specs
echo "/usr/local/lib/glbcc-lib/0.0.7/lib/lbcrt0.o" >> /usr/local/lib/glbcc-lib/0.0.7/specs
rm -f glbcc/glbcc.bas
echo -e "specs$ = \"/usr/local/lib/glbcc-lib/0.0.7/specs\"\nxspecs$ = \"/usr/local/lib/glbcc-lib/0.0.7/xspecs\"" \
	     | cat - glbcc/glbcc.tmpl > glbcc/glbcc.bas
make -C glbcc bootstrap
make[1]: Entering directory `/glbcc-0.1.0/glbcc'
../lbpp/src/lbpp -I../libLB/include -o glbcc.c glbcc.bas
gcc -Wall -g `gnome-config --cflags gnomeui` -I../libLB/include -o glbcc glbcc.c ../libLB/lib/lbcrt0.o -L../libLB/lib `gnome-config --libs gnomeui` -lLB -lm 
glbcc.c:12:2: **error: #error** -e specs$ = "/usr/local/lib/glbcc-lib/0.0.7/specs"
make[1]: *** [bootstrap] **Error 1**
make[1]: Leaving directory `/glbcc-0.1.0/glbcc'
make: *** [install] **Error 2**

---

