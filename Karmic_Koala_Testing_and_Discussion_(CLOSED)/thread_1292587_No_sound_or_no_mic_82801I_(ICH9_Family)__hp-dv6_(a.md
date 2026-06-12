---
title: "No sound or no mic 82801I (ICH9 Family)  hp-dv6 (and others) Karmic/Jaunty"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thelinuxfan on 2009-10-16
I have been trying to get both internal sound and mic working on an HP Pavilion dv6-1053 for awhile now. I read through a lot of posts and have seen no solid solutions. I am running Karmic 9.10, but this will work for Jaunty as well (untested on others.) This will work for other computers as well, you just have to match your codec from [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568). Just find your model.

First, my sound card and codec.

```
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

``````
cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD75B3X5
Codec: LSI ID 1040
Codec: Intel G45 DEVCTG

``````
lspci -v | less
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3627
        Flags: bus master, fast devsel, latency 0, IRQ 33
        Memory at da500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```1. Upgrade Alsa form the latest snapshot (instructions courtesy of ALPHO2K)
 [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

Installation :

To do this, we must begin by determining our version of alsa as follows :

```

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
```To avoid problems during the upgrade of Alsa-utils, we need to stop it with the following command :

```

sudo /etc/init.d/alsa-utils stop

```We must then install the necessary tools to compile along with the kernel headers :

```

sudo apt-get -y install build-essential ncurses-dev gettext xmlto
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev

```Then, we go in our personal folder and download alsa-driver, alsa-lib and alsa-utils :

```

cd ~
rm -rf ~/alsa*
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.21a.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.21.tar.bz2

```After that, we create a new folder for the compilation and installation of the 3 files. Then, we move the 3 tar files that we just downloaded in this folder :

```

sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .

```Unpack the 3 tar files :

```

sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*

```We compile and install alsa-driver :

```

cd alsa-driver*
sudo ./configure
sudo make
sudo make install

```We compile and install alsa-lib :

```

cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

```We compile and install alsa-utils :

```

cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

```If like me, you got this error during the last &#8220;sudo ./configure&#8221; :

checking form.h presence... yes
checking for form.h... yes
checking for new_panel in -lpanelw... no
configure: error: panelw library not found

You will need to add those symbolics links (only if you got the error) and restart the installation from the last &#8220;sudo ./configure&#8221; :

```

sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
sudo ln -s libncursesw.so.5 /lib/libncursesw.so

```Then, we remove the 3 tar files in our personal folder that are not anymore necessary :

```

rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*

```Then, just restart your computer and your alsa version should be 1.0.21!

You can verify that you have now indeed have this version of alsa :

```

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Aug 31 2009 for kernel 2.6.28-15-generic (SMP).

```2. Add the options to /etc/modprobe.d/alsa-base.conf

Open a terminal and do....

```
$ sudo gedit /etc/modprobe.d/alsa-base.conf
```Go to the bottom of the file and add the following line.

```
options snd-hda-intel model=dell-m4-3 enable_msi=1
```and then restart.

3. Adjust the mixer appropriately.

Open a terminal

```
$ alsamixer
```Make sure PCM, Master, and Speaker are up all the way.

hit f4 to go to [Capture]

turn everything up to 100% and make sure nothing is muted. The only keys you should have to press are up arrow and 'm' key (if muted.) 

On Input Source, set it to Digital Mic by pressing the 'Up' key.

**Capture 100% and Input Source set to Digital Mic are the only necessities.

Hit 'esc' to save.

Your mic should be working now.

4. I had a problem with alsamixer not saving after a reboot. I made a bash script and threw it in /etc/init.d/ to set everything right.

**I should note that I tried sudo alsactl store many times. It would not keep my saved configuration.

Open a text editor and enter:
```

#!/bin/bash

amixer set PCM 100%
amixer set Master 100%
amixer set Speaker 100%
amixer set Capture 100%
amixer cset iface=MIXER,name='Input Source' 2

```Save it as volumeAdjust.sh and do the following for it to run on boot.

```

$ sudo mv volumeAdjust.sh /etc/init.d/
$ sudo update-rc.d volumeAdjust.sh defaults
$ sudo chmod +x /etc/init.d/volumeAdjust.sh 

```Restart and you should be good to go.

---

### Post by alinuxfan on 2009-10-16
Great Howto! Thanks bro ;)

---

