---
title: "Midingsolo compile fails - .deb file?"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Ginjeet on 2008-02-26
Hello there!

Trying to install a WAV to MIDI software Midingsolo ( [https://gna.org/projects/midingsolo](https://gna.org/projects/midingsolo) )

running ./configure gives :

...
checking for sqrt... yes
checking whether QTDIR environment variable is set... no, try a default one (/usr/lib/qt3)
checking for Qt library...
configure: error: Qt library not found. Maybe QTDIR isn't properly set or wrong --with-Qt-dir parameter.

./configure QTDIR=/usr/lib/qt3 -> does not work...
Anybody can help me with compiling or giving me a deb file?

Ginjeet

---

### Post by Partyboi2 on 2008-02-26
try
```
export QTDIR=/usr/share/qt3
```
then
```
./configure
```

---

### Post by Ginjeet on 2008-02-27
That did the trick, but still....

"
checking whether to enable ALSA... yes
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.9... not present.
configure: error: Sufficiently new version of libasound not found.
"
(package libasound2 already installed)

I have no idea for this one. Will you please help me?

And also do you know a friendly tutorial on compiling? Because than I could figure it out myself. :)
Thanks for help!

Ginjeet

---

### Post by Partyboi2 on 2008-02-27
need to install  libasound2-dev
```
sudo apt-get install libasound2-dev
```[This]("https://help.ubuntu.com/community/CompilingSoftware") might give you some hints on compiling. Most programs you need to compile come with a install file that gives you directions on how to compile that program.

---

### Post by Ginjeet on 2008-02-27
configure went fine, make gives error:

Making all in Music
make[3]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs/Music'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..   -I/usr/share/qt3/include -Wall -ansi -I../../libs -DQT_THREAD_SUPPORT -O3 -ffast-math -DFANR_OUTPUT_MIDI -DFANR_OUTPUT_STDOUT -DCAPTURE_ALSA -DCAPTURE_JACK -MT Algorithm.o -MD -MP -MF ".deps/Algorithm.Tpo" -c -o Algorithm.o Algorithm.cpp; \
        then mv -f ".deps/Algorithm.Tpo" ".deps/Algorithm.Po"; else rm -f ".deps/Algorithm.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..   -I/usr/share/qt3/include -Wall -ansi -I../../libs -DQT_THREAD_SUPPORT -O3 -ffast-math -DFANR_OUTPUT_MIDI -DFANR_OUTPUT_STDOUT -DCAPTURE_ALSA -DCAPTURE_JACK -MT Convolution.o -MD -MP -MF ".deps/Convolution.Tpo" -c -o Convolution.o Convolution.cpp; \
        then mv -f ".deps/Convolution.Tpo" ".deps/Convolution.Po"; else rm -f ".deps/Convolution.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..   -I/usr/share/qt3/include -Wall -ansi -I../../libs -DQT_THREAD_SUPPORT -O3 -ffast-math -DFANR_OUTPUT_MIDI -DFANR_OUTPUT_STDOUT -DCAPTURE_ALSA -DCAPTURE_JACK -MT Correlation.o -MD -MP -MF ".deps/Correlation.Tpo" -c -o Correlation.o Correlation.cpp; \
        then mv -f ".deps/Correlation.Tpo" ".deps/Correlation.Po"; else rm -f ".deps/Correlation.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..   -I/usr/share/qt3/include -Wall -ansi -I../../libs -DQT_THREAD_SUPPORT -O3 -ffast-math -DFANR_OUTPUT_MIDI -DFANR_OUTPUT_STDOUT -DCAPTURE_ALSA -DCAPTURE_JACK -MT FreqAnalysis.o -MD -MP -MF ".deps/FreqAnalysis.Tpo" -c -o FreqAnalysis.o FreqAnalysis.cpp; \
        then mv -f ".deps/FreqAnalysis.Tpo" ".deps/FreqAnalysis.Po"; else rm -f ".deps/FreqAnalysis.Tpo"; exit 1; fi
FreqAnalysis.cpp:26:19: error: fftw3.h: Nincs ilyen fájl vagy könyvtár
make[3]: *** [FreqAnalysis.o] Error 1
make[3]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs/Music'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3'
make: *** [all] Error 2


that make no sense to me :(

Ginjeet

---

### Post by Partyboi2 on 2008-02-27
create the file that it is missing. To do that you need to create a empty file in /midingsolo/libs/music and name it fftw3.h. So for example if the midingsolo folder was in your home directory you would do something like 
```
>> /home/user/midingsolo/libs/music/fftw3.h
```
or you can just open up nautilus and navigate to the folder and create the empty file.

---

### Post by Ginjeet on 2008-02-28
It also asked for a "glut.h" file in /src/GL (I did "mkdir GL" and also in the dir "echo > glut.h") but than it says:

"
make[2]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..   -I/usr/share/qt3/include -I../libs -I../ui -DQT_THREAD_SUPPORT  -O3 -ffast-math -DFANR_OUTPUT_MIDI -DFANR_OUTPUT_STDOUT -DCAPTURE_ALSA -DCAPTURE_JACK -MT GLGraph.o -MD -MP -MF ".deps/GLGraph.Tpo" -c -o GLGraph.o GLGraph.cpp; \
        then mv -f ".deps/GLGraph.Tpo" ".deps/GLGraph.Po"; else rm -f ".deps/GLGraph.Tpo"; exit 1; fi
GLGraph.cpp: In member function ‘virtual void GLGraph::base_paint(float)’:
GLGraph.cpp:379: error: ‘GLUT_BITMAP_HELVETICA_12’ was not declared in this scope
GLGraph.cpp:379: error: ‘glutBitmapCharacter’ was not declared in this scope
make[2]: *** [GLGraph.o] Error 1
make[2]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3'
make: *** [all] Error 2
"

?

---

### Post by Ginjeet on 2008-02-28
Found Glut project + file glut37.zip
extracted it's contents of GL libraries to my midingsolo/src/GL than it went on, but:

```
make  all-recursive
make[1]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3'
Making all in m4
make[2]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/m4'
Making all in libs
make[2]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs'
Making all in CppAddons
make[3]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs/CppAddons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs/CppAddons'
Making all in Music
make[3]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs/Music'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs/Music'
make[3]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs'
make[2]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/libs'
Making all in ui
make[2]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3/ui'
make  all-am
make[3]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3/ui'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/ui'
make[2]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/ui'
Making all in src
make[2]: Entering directory `/home/ginjeet/Builds/midingsolo-0.1.3/src'
g++ -I../libs -I../ui -DQT_THREAD_SUPPORT  -O3 -ffast-math -DFANR_OUTPUT_MIDI -DFANR_OUTPUT_STDOUT -DCAPTURE_ALSA -DCAPTURE_JACK   -o midingsolo  ANR.o CustomMainForm.o View.o GLGraph.o GLRTGraph.o GLPolyGraph.o CaptureThread.o GLComponents.o GLMonoGraph.o main.o CaptureThread_moc.o CustomMainForm_moc.o GLGraph_moc.o GLRTGraph_moc.o GLPolyGraph_moc.o GLComponents_moc.o GLMonoGraph_moc.o ConfigForm.o ConfigForm_moc.o MainForm.o MainForm_moc.o ../libs/Music/libMusic.a ../libs/CppAddons/libCppAddons.a -lGLU -lGL  -lSM -lICE  -lX11 -lXext -lXmu -lXt -lXi   -ljack -lasound -lm -ldl -lpthread -lqt-mt -L/usr/share/qt3/lib -L/usr/share/qt3/lib64
GLGraph.o: In function `GLGraph::base_paint(float)':
GLGraph.cpp:(.text+0x2a29): undefined reference to `glutBitmapHelvetica12'
GLGraph.cpp:(.text+0x2a32): undefined reference to `glutBitmapCharacter'
GLComponents.o: In function `GLComponents::paintGL()':
GLComponents.cpp:(.text+0xa22): undefined reference to `glutBitmapHelvetica12'
GLComponents.cpp:(.text+0xa2b): undefined reference to `glutBitmapCharacter'
GLComponents.cpp:(.text+0xe79): undefined reference to `glutBitmapHelvetica10'
GLComponents.cpp:(.text+0xe82): undefined reference to `glutBitmapCharacter'
GLMonoGraph.o: In function `GLMonoGraph::paintGL()':
GLMonoGraph.cpp:(.text+0xf5b): undefined reference to `glutBitmapHelvetica12'
GLMonoGraph.cpp:(.text+0xf64): undefined reference to `glutBitmapCharacter'
main.o: In function `main':
main.cpp:(.text+0x254): undefined reference to `glutInit'
collect2: ld returned 1 exit status
make[2]: *** [midingsolo] Error 1
make[2]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ginjeet/Builds/midingsolo-0.1.3'
make: *** [all] Error 2
```

Really no idea this time.

Ginjeet

---

