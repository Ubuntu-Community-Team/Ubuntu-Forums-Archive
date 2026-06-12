---
title: "[SOLVED] OSS and ALSA"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by fallenfantasyx on 2008-02-04
Today i installed the new OSS driver since i have an XFI card thats been collecting dust inside my computer, anyway after a little trouble getting it installed i finally got it installed. Now when i go to configure my sound device through gnome it doesnt detect any devices and i have no sound on tests, i ran oss info and the output is as follows...

Version info: OSS 4.0 (b1013/200802012055) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 (WindowsSucks)

Number of audio devices:        11
Number of audio engines:        27
Number of mixer devices:        2


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=79348 (227359)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086284b
    Subvendor ID 0x147b1082
     Codec  0: ALC888 (0x10ec0888/0x147b0000)
 2: sbxfi0 Sound Blaster X-Fi (SB073x) interrupts=226939 (226939)
    PCI device 1102:0005, subdevice 1102:0031
 3: ossusb0 USB audio core services
 4: vmix0 OSS transparent virtual support


Mixer devices
 0: High Definition Audio ALC888 (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (SB073x) (Mixer 0 of device object 2)

Audio devices
High Definition Audio front       /dev/oss/hdaudio0/pcm0  (device index 0)
High Definition Audio rear        /dev/oss/hdaudio0/pcm1  (device index 1)
High Definition Audio center/LFE  /dev/oss/hdaudio0/pcm2  (device index 2)
High Definition Audio side        /dev/oss/hdaudio0/pcm3  (device index 3)
High Definition Audio pcm4        /dev/oss/hdaudio0/pcm4  (device index 4)
High Definition Audio spdif-out   /dev/oss/hdaudio0/spdout0  (device index 5)
High Definition Audio rec1        /dev/oss/hdaudio0/pcmin0  (device index 6)
High Definition Audio rec2        /dev/oss/hdaudio0/pcmin1  (device index 7)
High Definition Audio spdif-in    /dev/oss/hdaudio0/spdin0  (device index 8)
Sound Blaster X-Fi (SB073x) output  /dev/oss/sbxfi0/pcm0  (device index 9)
Sound Blaster X-Fi (SB073x) input  /dev/oss/sbxfi0/pcmin0  (device index 10)




ANY Ideas?!

---

### Post by thepocketdrummer on 2008-02-05
I am also having issues. When I try to reinstall it, it says it fails. When I try to UNinstall it, that also fails. The message says...
```
E: oss-linux: subprocess pre-removal script returned error exit status 2
```

Details reading...

```
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linus (--purge):
subprocess pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: no such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
no /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
oss-linux
``` .... they should make a way to copy text in details... typing all that sucks...

The instructions say, 

```
Installation on Linux:
WARNING: Linux 2.6 kernel with kernel sources (or kernel headers), GCC Compiler, Binutils,
GNU Make, GTK/GLIB 2.0 libraries must be installed before you can install OSS. Please consult
your Linux distributor’s manuals on how to install and prepare the kernel sources so that external
drivers and modules can be compiled for your kernel.


1. Log on as root in Console Session (if yo
   u're logged in Gnome/KDE,
   you'll need to exit and press
   <Ctl><Alt><F1> and log in on the
   Console)

DEB package
dpkg –I oss-linux_v4.0-
123_i386.deb

2. You will have to reboot the system if
   OSS replaced any driver previously
   detected.
3. To test that the audio package is
   correctly installed type: osstest and you
   should hear the test sounds on the front
   left, right and both speakers. Now log
   out of the console session

```

I tried this, but I can't figure out how to do the dpkg part. I'm new at linux.

When I check the soundon.log file, it says this...

```
Open Sound System starting Mon Feb 4 23:18:36 CST 2008
OSS version: 
Kernel version:  2.6.22-14-generic
Kernel vermagic:  2.6.22-14-generic SMP mod_unload
No /usr/lib/oss/etc/installed_drivers - running ossdetect
Still no /usr/lib/oss/etc/installed_drivers - cannot continue
```

I got the original instructions from [http://ubuntuforums.org/showthread.php?t=571656&highlight=XFI]("http://ubuntuforums.org/showthread.php?t=571656&highlight=XFI")

instructions from OSS here:
[http://www.opensound.com/download.cgi]("http://www.opensound.com/download.cgi")

PLEASE help.

---

### Post by fallenfantasyx on 2008-02-05
yea no luck yet, any ideas?

i found that when i run osstest i hear sound, and when something is playing if i go into ossxmix my onboard soundcard is recieving sound but isnt outputting it.

---

### Post by thepocketdrummer on 2008-02-05
I actually contacted OSS support (yeah, they actually have support!), and they gave me these two websites...

[This one tells you how to recover from a failed .deb installation.]("http://www.4front-tech.com/forum/viewtopic.php?t=2054")

[This one is what he told me to do to set it up afterwards.]("http://www.4front-tech.com/forum/viewtopic.php?t=1438")

I hope this helps. I'm fairly new at this, so I couldn't begin to understand what might be causing your problem. But, in the event that this fixes both our problems, we can rejoice together! :lolflag:

---

### Post by fallenfantasyx on 2008-02-05
i figured it out at least for me, i disabled my onboard audio via the bios, it allowed the drivers to work im not getting 5.1 sound just my left and right but thats for another day i guess...

---

### Post by thepocketdrummer on 2008-02-05
> **fallenfantasyx said:**
> i figured it out at least for me, i disabled my onboard audio via the bios, it allowed the drivers to work im not getting 5.1 sound just my left and right but thats for another day i guess...

Yeah, I just did that and reinstalled. My audio works, but it seems to turn on before playing the sound, then turn off again. Not to mention that the volume controls on my keyboard and at the top right of the screen don't work. It says, 

```
No volume control GStreamer plugins and/or devices found.
```

Any clue how to fix that? :confused:

I made a little script to let me get into OSSXMIX easier. I can change the volume there, but it's not exactly ideal. Now, Ardour refuses to create a new session. :_(

---

### Post by dvord on 2008-02-07
I am now in the same boat.

Gstreamer doesn't seem to like the OSS update from what it looks like.  I can't play any system sounds, but I do hear stuff when I run the tests.

The volume was terribly loud.  I ran ossmix play XX  (where XX is the DB, mine are now 13 run ossmix without params if you want to see current settings).

Played an MP3 just fine.  I did read on[ 4front]("http://4front-tech.com/forum/viewtopic.php?p=7485#7485") that someone else was having this mixer issue as well.

Sound solved, yes, but still need help with Gstreamer.  Time for another post?

Edit: Run ossxmix for the GUI mixer.  That might help some.

---

