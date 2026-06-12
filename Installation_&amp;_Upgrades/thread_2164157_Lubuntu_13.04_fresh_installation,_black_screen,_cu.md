---
title: "Lubuntu 13.04 fresh installation, black screen, cursor flashing"
date: 2013-07-30
forum: Installation &amp; Upgrades
---

### Post by A4Kke6k on 2013-07-30
Hey I’m trying to install  Lubuntu (alternate install) 13.04 on my notebook for nearly a week :(

My notebook is a Compaq Armada E500:


CPU: Pentium 3 800Mhz
RAM: 256MB
HDD: 30GB
Chipset: Intel 440BX
Graphic: ATI rage mobility AGP 2x Series (rev 64) 8MB

The problem after installation from CD finishes is that I don’t get to the login screen.


The display shows me Lubuntu starting screen for some seconds then I only see a blinking cursor on the left top of the screen.
In this sad state my notebook remains till I reboot or shut it down.

By pressing “ctrl + alt + del” I get the message” acpid: exiting”  and the nice Lubuntu screen before computer restarts.

I verified the MD5 checksum of the CD, seems to be ok.

I tried to boot with “acpi=off”, “nomodeset”, “xforcevesa” but nothing helped … well I’m not sure if I wrote the boot options correctly into the grub bootloader.
I selected the first entry “Ubuntu” pressed “e” and searched for the line starting with “linux /boot/vmlinuz” (according to [http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting](http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting)).
Before the expression “quit splash” I added each option separated with a blank.

Any ideas? I’m not familiar with linux…

---

### Post by sudodus on 2013-07-31
Welcome to the Ubuntu Forums :-)

Your computer is very old, maybe too old for Lubuntu 13.04. I think you have been doing the right things, installing from the alternate iso and trying with the boot options.

I want to add a few tips:

0. Remove the boot options **quiet splash**.

1. Try if it runs with the boot option **text** (instead of and together with **nomodeset**).

2. Try the older version ***Lubuntu 12.04*** (which has end of life in October) and if it works, try ***LXLE***, a fork of Lubuntu 12.04, that promises long time support until April 2017. Chances are that the graphics drivers of 12.04 support your hardware better.

3. Try some other distro that is known to work well with old hardware, ***Knoppix*** or ***Puppy***.

See also this link [Old hardware]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by A4Kke6k on 2013-07-31
Thanks for your tips. 

0. Bootoption: quiet splash

Yields to a fast text output I can't read. then the known problem occurs. Cursor is blinking. If i press "ctlr + alt+ F1"
there is a flickering message "*starting crash report deamon [OK]"

1. Bootoption: "text nomodeset" brings mit to textual login prompt

I tried to start desktop with "startx / sudo startx":

```

...
Loading extension GLX
The XKEYBOARD keymap compiler (xkbcomp) reports:
>Warning:    Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>        Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE)
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0xb7710f49]
(EE) 1: /usr/bin/X (0xb7563000+0x1b1e86) [0xb7714e86]
(EE) 2: (vdso) (__kernel_rt_signaturn+0x0) [0xb754040c]
(EE) 3: /lib/i386-linux-gnu/libc.so.6 (0xb7149000+0x7fed6) [0xb71c8ed6]
(EE) 4: ?? [0xb8270387]
(EE)
(EE) Segmentation fault at adress 0x0

Fatal server error:
Caught signal 11 (Segmentation fault). Server aborting

(EE)
Please consult The X.Org Foundation support
    at http://wiki.x.org
    for help.

(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information
(EE)
Server terminated with error (1). Closing log file.
xinit: connection to X server lost

```

1.1 Bootoption: "text" 
same as 1.

2. 
I had installed 12.04 few days ago which had the same errors, but I didn't tried the things you told me there ... at present I don't want to reinstall ubuntu it lasts long on my notebook.
    LXLE: Maybe I misunderstood you here, I thought lxde is a good lightweight desktop environment. LXLE needs 512MB RAM :-( ([http://lxle.net/index.php?id=support](http://lxle.net/index.php?id=support))


3. 
I think I try a live CD from Knoppix in the evening.

---

### Post by sudodus on 2013-07-31
I think you have problems with the graphics driver. Obviously there are problems also with 12.04.

- One possibility is to boot in text mode (as you did successfully), and install a proprietary driver for your ATI Rage chip/card (and reboot).

- But I would encourage you to try Knoppix tonight. Chances are that it will work out of the box. Otherwise there are many 'cheat codes' for Knoppix corresponding to Ubuntu's 'boot options'. See the documentation at the Knoppix web pages.

---

### Post by gordintoronto on 2013-07-31
Your computer does not have enough memory to install Lubuntu 13.04.

See: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

