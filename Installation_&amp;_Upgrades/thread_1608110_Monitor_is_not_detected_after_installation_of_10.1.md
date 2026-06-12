---
title: "Monitor is not detected after installation of 10.10"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2010-10-28
Hello everyone :-)

I just upgraded, and when I rebooted I could see that it was booting but after the initial phase I got a blank screen.

I went to prompt and tried xrandr to which I got the error :
Can't open display.

What does that mean, and how do I fix this?
I guess that my monitor is not properly identified or is not identified at all.

Does anyone know what I can do?

Went to /etc/gdm to find xorg.conf but it is not there.
In etc/X11 I have an xorg.conf

The contents are :

Section "Monitor"
Identifier   "Configured Monitor"
EndSection

Section "Screen"
            Identifier     "Default Screen"
            Monitor        "Configured Monitor"
            Device         "Configured Video Device"
            DefaultDepth    24
EndSection

Section "Module"
          Load   "glx"
EndSection

Section "Device"
         Identifier    "Configured Video Device"
         Driver "nvidia"
         Option "NoLogo"   "True"
EndSection

---

### Post by Ifaistos on 2010-10-28
bump...

---

### Post by Ifaistos on 2010-10-29
bump...

---

### Post by Ifaistos on 2010-10-29
bumpity bump....

---

### Post by Ifaistos on 2010-10-30
I noticed that a lot of people had the same problem with me.
I tried a lot of different solutions but none of them worked.
It seems that all of them involved changing the grub.

I was using grub instead of grub2, and xorg.conf.

Anyway, I had not done a clean install since 6.04.  I guess that 4 and 1/2 years is a long time, and my installation was a bit cluttered, after all those upgrades.

I decided to do a clean install, which worked flawlessly and now everything is working fine.

Just wanted to mention that just in case more people have the same problem as me.

Thanks everyone
Linux Rocks!!

ps1. I noticed that I am not using now grub, and xorg.conf.  

ps2. I installed everything in less than two hours (including backup) while doing various other things.  Now my computer is fully functional as it was.

ps3. I also had to do a clean install of Windows 7, for my wifes computer.  Although they look nice, it will take me at least two days to bring the computer in workable order.  I will need a LOT of time to install Office, CD/DVD burning, e-mail clients, skype, antivirus, fax software, scan software, Multimedia players of my choice ... and the list is endless.  Plus I have to activate and find codes... The task is huge, and the difference with 10.10 is enormous.

---

### Post by mixmastamyk on 2010-10-30
I'm a bit late here, but "Can't open display" means X isn't available from that terminal, could be for various reasons.

To speed up windows installs, head to [http://ninite.com/](http://ninite.com/)  They can make you a custom automated installer with 50 or so favorite programs.

-Mike

---

