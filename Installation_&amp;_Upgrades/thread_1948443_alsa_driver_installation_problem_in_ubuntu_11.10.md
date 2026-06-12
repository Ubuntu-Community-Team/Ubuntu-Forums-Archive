---
title: "alsa driver installation problem in ubuntu 11.10"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by newera on 2012-03-28
hello friends,
i'm a newbie in linux.. i have installed ubuntu 11.10 a week ago and having no audio. my motherboard is biostar g41d3+ and uses intel hda sound (ich7 ver1). there are no other sound cards, only on-board audio. the sound settings show 'dummy stereo' in the output tab. i've downloaded latest alsa drivers from [http://www.alsa-project.org](http://www.alsa-project.org) (alsa 1.0.25) and followed the instructions in [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel). 

im stuck here when installing driver
sudo ./configure --with-cards=hda-intel --with-sequencer=yes ; make ; make install

the terminal shows 

checking...
.
.
.
.
here are the last lines

config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.25'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.25/include'
make -C sound prepare
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
make prepare2
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
ln -s ../../alsa-kernel/include/aci.h
ln: creating symbolic link `./aci.h': Permission denied
make[4]: *** [aci.h] Error 1
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
make[3]: *** [prepare] Error 2
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
make[2]: *** [prepare] Error 2
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25/include'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25'
make: *** [include/sndversions.h] Error 2
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /usr/src/alsa/alsa-driver-1.0.25/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
rm: cannot remove `/usr/include/sound': Permission denied
install: cannot change owner and permissions of `/usr/include/sound': Operation not permitted
install: cannot change ownership of `/usr/include/sound/ac97_codec.h': Operation not permitted
make: *** [install-headers] Error 1

Please help me out... thanks in advance..

---

### Post by newera on 2012-03-29
hello friends,
i'm a newbie in linux.. i have installed ubuntu 11.10 a week ago and  having no audio. my motherboard is biostar g41d3+ and uses intel hda  sound (ich7 ver1). there are no other sound cards, only on-board audio.  the sound settings show 'dummy stereo' in the output tab. i've  downloaded latest alsa drivers from [http://www.alsa-project.org]("http://www.alsa-project.org/") (alsa 1.0.25) and followed the instructions in [http://www.alsa-project.org/main/ind...dule-hda-intel]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel"). 

im stuck here when installing driver
sudo ./configure --with-cards=hda-intel --with-sequencer=yes ; make ; make install

the terminal shows 

checking...
.
.
.
.
here are the last lines

config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.25'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.25/include'
make -C sound prepare
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
make prepare2
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
ln -s ../../alsa-kernel/include/aci.h
ln: creating symbolic link `./aci.h': Permission denied
make[4]: *** [aci.h] Error 1
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
make[3]: *** [prepare] Error 2
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
make[2]: *** [prepare] Error 2
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25/include'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25'
make: *** [include/sndversions.h] Error 2
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /usr/src/alsa/alsa-driver-1.0.25/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
rm: cannot remove `/usr/include/sound': Permission denied
install: cannot change owner and permissions of `/usr/include/sound': Operation not permitted
install: cannot change ownership of `/usr/include/sound/ac97_codec.h': Operation not permitted
make: *** [install-headers] Error 1

Please help me out... thanks in advance..

---

### Post by mörgæs on 2012-03-30
Please don't double-post. 
Merged.

---

### Post by newera on 2012-04-01
sorry.. i wanted that thread in ubuntu. its happened when i tried to post in a new location. 
please help me out ... do you have any solution sir..

---

### Post by ben91 on 2012-04-11
why shouldn't he double post if simply nobody gives a da*n about his problem...so much for the "humanity" in the word ubuntu...

---

### Post by mörgæs on 2012-04-11
Because double-posting buries other questions (leading to even bigger urge to double-post) and because we in general don't like the 'me first' attitude. 

If you want to suggest double-posting being allowed you should open a thread in [Forum Feedback & Help]("http://ubuntuforums.org/forumdisplay.php?f=48"). Or, maybe even better, you could answer original poster.

If a question does not get enough attention this [guide]("http://ubuntuforums.org/showthread.php?t=1422475") is worth reading.

---

