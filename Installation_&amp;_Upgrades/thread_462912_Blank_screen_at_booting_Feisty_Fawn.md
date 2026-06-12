---
title: "Blank screen at booting Feisty Fawn"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by tomislav on 2007-06-03
Hello,

I have a problem with the lastest Ubuntu, 7.04 Feisty Fawn. I have the Live CD for i386.

**Quick intro:** I have 2 computers. The first is the one I use all the time, it's good and everything although not state of the art. Anyways, I've managed to boot Feisty Fawn on this computer. The second computer, which is much weaker, is the problem. 

**Specs of the computer in question:** I've included the DxDiag.txt for the computer since I don't know which information could be of use to those who are willing to help me. It's zipped since it exceeded the maximum file size for text files.

**Problem:** I insert the Feisty Fawn into my computer and restart it. The CD boots normally and I see the Ubuntu starting screen. I choose option 1 (boot and install, I think that's what it says can't remember). Then I see the Ubuntu logo and that orange polygon that goes from left to right. After some time the progress bar starts getting filled and once it does my screen goes black. I've tried waiting for hours once just in case my slow comp needs time to load everything. I've tried the following: Checking the CD for errors (everything alright there), starting in safe graphics mode, checking the help. I've also successfully booted Mandriva One Live CD on this computer, if that's any help.

[FONT="Arial Black"][SIZE="4"][COLOR="SeaGreen"]Please help! [/COLOR][/SIZE][/FONT]

---

### Post by wpshooter on 2007-06-03
After what you have already tried, I would suggest that you download, burn, test and try the ALTERNATE CD version.

---

### Post by tomislav on 2007-06-03
Do you think I should download the 6.06 Ubuntu and try that?

---

### Post by tomislav on 2007-06-03
Btw, I tried booting Ubuntu in verbose mode and here's what the computer printed just before the screen went black:

```
Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon
Starting network events dispatcher NetworkManager
Starting System Tools Backends system-tool-back(ends I suppose, haven't seen the end of this line)
Starting GNOME Display Manager...
Starting Common Unix Printing System: cupsd
```

I suppose GNOME should've gone up just after that...

---

### Post by wpshooter on 2007-06-03
> **tomislav said:**
> Do you think I should download the 6.06 Ubuntu and try that?

I believe I would try either Edgy or Dapper but probably not Feisty.

---

### Post by Topsiho on 2007-06-03
I have the same nvidia graphics card so maybe my /et/X11/xorg.conf file may be interesting to you, from which I copy here the relevant part:

====
Section "Device"
  identifier "Generic Video Card"
  boardname "RIVA TNT2"
  busid "PCI:0:6:0"
  driver "nv"
  screen 0
  vendorname "RIVA"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Generic"
  modelname "1024x768 @ 60 Hz"
  HorizSync 31.5-48.5
  VertRefresh 50-70
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Generic Video Card"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1024x768@60" "1152x768@54" "800x600@60" "1280x854" "800x600@56" "640x480@60"
  EndSubSection

EndSection
====

You can check, in a console (CTRL-ALT-F1) what differences there are with your own xorg.conf file and edit it accordingly. My screen is a flat panel SyncMaster screen.


Hope this helps,

Topsiho

---

### Post by tomislav on 2007-06-03
Sorry I have no clue what xorg.conf is. I have Windows installed so if it's from Linux I won't be able to get it.

> **wpshooter said:**
> I believe I would try either Edgy or Dapper but probably not Feisty.

Is Dapper also on a Live CD?

---

### Post by armaud on 2007-06-03
Hello
     I have been waiting for a solution to my problem for quuite some time now. Since i have a similar problem i thought maybe some one will help me. My computer is P4 2.4G 512 M ram. I installed ubuntu 6.06 and it worked perfectly. Then i decided to shift to 7.04. I installed first kubuntu twice then ubuntu twice but each time i have the same problem. As soon as i choose Ubuntu from Grub, my screen goes blank and remains blank for nearly 5 mins. Then all of a sudden the screen asking for password appears. Then my computer runs fine. The screen which shows ubuntu loading at startup never appears. I saw the system log and i saw the following lines repeating 2 to 3 times.This is only some portion as actual system log is very long. I have posted my problem in absolute beginner section. You can see it by searching for 'Kubuntu 7.04 startup problem'. Please keep in mind that i am a novice to Ubuntu so please explain.


May 28 18:51:01 maud-desktop kernel: [ 199.666781] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 28 18:51:05 maud-desktop gconfd (armaud-5334): starting (version 2.18.0.1), pid 5334 user 'armaud'
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 1
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 28 18:51:15 maud-desktop gconfd (armaud-5334): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 0
May 28 18:53:06 maud-desktop gconfd (root-5548): starting (version 2.18.0.1), pid 5548 user 'root'
May 28 18:53:06 maud-desktop gconfd (root-5548): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 28 18:53:06 maud-desktop gconfd (root-5548): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 28 18:53:06 maud-desktop gconfd (root-5548): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 28 18:53:06 maud-desktop gconfd (root-5548): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 28 18:53:06 maud-desktop gconfd (root-5548): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 28 18:53:36 maud-desktop gconfd (root-5548): GConf server is not in use, shutting down.
May 28 18:53:36 maud-desktop gconfd (root-5548): Exiting
May 28 18:56:06 maud-desktop gconfd (armaud-5334): Failed to send buffer
May 28 18:56:29 maud-desktop gconfd (root-5777): starting (version 2.18.0.1), pid 5777 user 'root'
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 28 18:57:29 maud-desktop gconfd (root-5777): GConf server is not in use, shutting down.
May 28 18:57:29 maud-desktop gconfd (root-5777): Exiting
May 28 18:57:40 maud-desktop gconfd (root-5856): starting (version 2.18.0.1), pid 5856 user 'root'
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 28 19:03:10 maud-desktop gconfd (root-5856): GConf server is not in use, shutting down.
May 28 19:03:10 maud-desktop gconfd (root-5856): Exiting
May 28 19:03:16 maud-desktop gconfd (armaud-5334): Exiting
May 28 19:03:25 maud-desktop exiting on signal 15
May 28 19:06:39 maud-desktop syslogd 1.4.1#20ubuntu4: restart.
May 28 19:06:40 maud-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic
May 28 19:06:40 maud-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
May 28 19:06:40 maud-desktop kernel: Symbols match kernel version 2.6.20.
May 28 19:06:40 maud-desktop kernel: No module symbols loaded - kernel modules not enabled.
May 28 19:06:40 maud-desktop kernel: [ 0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)

---

### Post by diatribe on 2007-06-03
try editing /boot/gtub/menu.lst, at the entry where it has your first kernel try adding:

vga=791 splash quiet

that should your splash show up

---

### Post by T999NNY on 2007-06-03
Its all a bit familiar to me this. I am really, really trying to like Linux but time after time when I try and install it I hit installation problems or driver problems etc. Just tried installing 7.04 and just like the other posters here I get the black screen of death. The CD loads fine and then just halts on a black screen. We don't want to be editing code to get things running, we just want to bang the CD in and it works! I am a windows system builder and pretty familiar with loading systems and rarely have any problems. Don't want to harp on but lets get this sorted out.

I really want this to work.......
Cheers T

---

### Post by tomislav on 2007-06-03
Seems this is a problem that affects older configurations... My primary comp runs the new Ubuntu just fine.

But I agree with you, this should really be sorted out.

I was hoping someone would go through my dxdiag.txt to see if some hardware components were not compatible with Ubuntu.

---

### Post by tomislav on 2007-06-05
Tried Dapper Drake and it's working. Very, very slow but at least something... :) I'll try and install it soon.

---

### Post by jvalente on 2007-06-22
If you have an ATI graphic card you can install the drivers and then initialize serverx:
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Then go CTRL-ALT-BACKSPACE

---

