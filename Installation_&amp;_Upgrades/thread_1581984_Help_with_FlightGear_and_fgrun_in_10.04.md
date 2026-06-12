---
title: "Help with FlightGear and fgrun in 10.04"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by cjmabry25 on 2010-09-25
**Originall Posted in Gaming & Leisure, then realized that probably wasn't the best place.**

I have tried and tried and tried. I've been compiling FlightGear from source and trying to get 2.0 to work for 4 or 5 hours, and I finally got it working with the PlayDeb .deb. Now to fgrun. I've tried compiling but on make I get, after some succesful things:

Code:
/fgrun_pty.Tpo"; exit 1; fi
g++ -DLOCALEDIR=\"/usr/local/share/locale\" -g -O2   -o fgrun  wizard.o wizard_funcs.o advanced.o advanced_funcs.o AirportBrowser.o AirportTable.o Fl_Table.o Fl_Table_Row.o Fl_OSG.o Fl_Heading_Dial.o main.o io.o fgfsrc.o logwin.o parkingloader.o settings.o util.o run_posix.o fgrun_pty.o -lsgmodel -lsgscreen -lsgprops -lsgxml -lsgdebug -lsgbvh -lsgmaterial -lsgmodel -lsgutil -lsgstructure -lsgprops -lsgtgdb -lsgmath -lsgmisc -lsgbvh -lsgio -lsgbucket -lsgmodel -lsgutil -lplibsg -lplibul -lplibnet -losgParticle -losgSim -losgViewer -losgGA -losgText -losgDB -losgUtil -losg -lOpenThreads -lfltk_gl -lpthread -lfltk -lGL -lXmu -lXt -lSM -lICE -lXi -lXext -lX11  -lm -lz -lutil -losgFX
/usr/bin/ld: cannot find -lsgbvh
collect2: ld returned 1 exit status
make[2]: *** [fgrun] Error 1
make[2]: Leaving directory `/usr/local/src/fgrun-1.5.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/local/src/fgrun-1.5.2/src'
make: *** [all-recursive] Error 1
And I'm stuck. Any suggestions? Also, when I run nice terrasync -p 5500 -S -d "$HOME/fgfsScenery" as stated to do here -http://wiki.flightgear.org/index.php/TerraSync, nothing happens, and I'm guessing it's because of the playdeb install. I ditched my succesful Arch install to get this working because I had no luck in Arch. I hope I can get it working haha

Thanks

---

