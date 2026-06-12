---
title: "LIRC DViCO USB Problem with Feisty - Please help"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by log on 2007-06-30
Hi guys,

I have tried everything! dmesg gives this: 

[   13.098072] hiddev96: USB HID v1.10 Device [DVICO DVICO USB HID Remocon V1.00] on usb-0000:00:1d.0-1


I have tried installing lirc from source and using the apt-get version. Both didnt work :(

I can never seem to get any device anywhere when I run

cat /proc/bus/input/devices


Has anyone set up a DViCO USB remote in feisty? How did you do it?

---

### Post by leftclick on 2007-10-14
I have also suffered from this problem and have just solved it.  Here is what I did:

1. Forget about the apt-get version of lirc.  Remove it if you have installed it already: 
[FONT="Courier New"]$ apt-get remove lirc lirc-x[/FONT]

2. Get the latest version from lirc.org (I used 0.8.2) and unpack:
[FONT="Courier New"]$ wget [http://optusnet.dl.sourceforge.net/sourceforge/lirc/lirc-0.8.2.tar.bz2](http://optusnet.dl.sourceforge.net/sourceforge/lirc/lirc-0.8.2.tar.bz2)
$ tar -jxvf lirc-0.8.2.tar.bz2[/FONT]

4. Ensure you have the dependencies.  If you get errors at the next step, chances are you have unmet dependencies.  I had just installed this system and everything else was configured from apt-get so I had to do an: 
[FONT="Courier New"]$ apt-get install g++ libx11-dev[/FONT]

5. Configure:
[FONT="Courier New"]$ cd lirc-0.8.2
$ ./setup.sh[/FONT]

6. Select 8-USB devices, 9-DVICO, then go back, check options under 2-Software configuration are to your liking, then back again and select 3-Save and run configure.

7. Build and Install:
[FONT="Courier New"]$ make
$ sudo make install[/FONT]

8. I had some problems getting irxevent to install, here's what I did for that:
[FONT="Courier New"]$ cd tools
$ make irxevent
$ cp irxevent /usr/local/bin/[/FONT]

9. Create a symbolic link to where LIRC thinks the HID device is:
[FONT="Courier New"]$ sudo mkdir /dev/usb
$ sudo ln -s /dev/hiddev0 /dev/usb/hiddev0[/FONT]

Now you can start lircd and run irw and you will see the buttons you press echoed on the terminal window.  Then you just need your config files which you can download and your lircrc file.

HTH
Ben

[Edit: Added libx11-dev as dependency.  It will compile without it but if you want irxevent, you need to include this library as well.  Also did some tidy-up; broke steps up a bit]

---

### Post by leftclick on 2007-10-31
Just a follow-up...  I never did get irxevent to work so anyone reading the above, please ignore the irxevent stuff.  I ended up not needing it anyway, irexec gave me another alternative in every case.

I also had to recreate the link under /dev on each boot, so I modified the /etc/init.d/lirc file to do this.  Here is my new version (attached).  (Sorry I don't have the original so I can't give a diff).

---

