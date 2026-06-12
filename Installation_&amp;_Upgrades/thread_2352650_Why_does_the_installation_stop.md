---
title: "Why does the installation stop?"
date: 2017-02-14
forum: Installation &amp; Upgrades
---

### Post by LuJo on 2017-02-14
After buying a new motherboard, processor, HDD and RAM, I can't install any of several Ubuntu versions, but Windows 8 works. How can I find out the reason? I sometimes manage to be able to see all sorts of stuff loading and starting, but then the screen goes dark and a turning symbol appears, that I can move with the mouse, but then the symbol stops turning and I can't do anything anymore. I used to think it had to do with Windows, so I deleted the partition with a G'-parted CD, but the Problem remained. I also wondered if it had to do with the DVD drive, because in Windows it was listed as a CD drive. A couple of times I got a bit further, had the desktop or the window with 'install Ubuntu' on it, but after the click it froze. I also tried Linux Mint and Xubuntu.
I think I've already wasted about 20 hours on this, although for 10 years I've never had major problems with a linux installation.

---

### Post by RobGoss on 2017-02-14
You might want to tell us a bit more about the hardware on your machine 

Have you tried using a USB device for the installation it might be a better option

---

### Post by LuJo on 2017-02-14
I downloaded a programm for a bootable USB stick on my laptop und then tried it, but the device does not show up in Bios as a boot option.
[http://www.asrock.com/mb/NVIDIA/N68C-GS4%20FX/](http://www.asrock.com/mb/NVIDIA/N68C-GS4%20FX/)  is my motherboard. 
Is it possible that a DVD drive will only read up to a certain point of a DVD? Is there still a Linux version that runs off a CD? My G-parted CD and Ubuntu repair CD both started.

---

### Post by LuJo on 2017-02-14
I found an old Ubuntu on a CD and it worked! Is there a way to find out whether my player is broken or just not recognized correctly (CD instead of DVD)?

---

### Post by QIII on 2017-02-14
Hello!

Sure sounds like a hardware problem.  (With the information provided, however, it is impossible to tell if the problem is simply that you have a CD drive.)

What might fit on a CD is a minimal install.  You could build up from there.  I know that sounds like a pain, but it's better than an old, unsupported release or just not being able to install at all.

---

### Post by LuJo on 2017-02-14
The worst case would be to buy another DVD drive, but maybe the problem is the motherboard or BIOS. I also tried the DVD ROM drive from another Computer, but it did not recognize the installations DVD at all. Could it be that a setting in BIOS is wrong? The HDD is on a SATA connector, the DVD Drive on a IDE connector. In BIOS I can read  CD/DVD, and I have used the drive for other Ubuntu installations. Windows also categorized it as CD.

---

### Post by ajgreeny on 2017-02-14
I note that the MB has an integrated nvidia graphics chip so you may need to hit F6 when you have got past the language selection part of the boot to DVD and from there choose the "nomodeset" boot-option.

It may allow only a low resolution GUI but at least it may allow the installation to carry through to the end.

---

### Post by LuJo on 2017-02-14
I didn't get to a language choice, tried F6 anyway. I checked the RAM (Memtest) and the DVD and it was all OK, so it seems that the DVD Drive must be able to read through the complete DVD, to be able to compare all the checksums. Ubuntu 12.4 on a CD installs quick, but without LAN. I put in a film DVD and I could open it and see all the folders. Couldn't play it because no codecs. Doesn't anyone have an idea?

---

### Post by oldos2er on 2017-02-14
> Doesn't anyone have an idea? 						 Please tell us your hardware specs.

---

### Post by LuJo on 2017-02-15
I'm not at home now, but the link to my board is above. Otherwise I have 8Gb RAM, and a 250GB HDD, and of course the DVD read/write drive. The HDD is connected with a SATA cable, the DVD with IDE.
Isn't there some kind of Boot-log, that shows errors? Or maybe there is some a command that gives information (clues) about the DVD drive?

---

### Post by LuJo on 2017-02-16
Now I managed to boot from USB and can get to the live-desktop. With disabled graphics  or 'nomodeset' I even got to the partition table, and it even started installing, but so slowly, it probably would have taken 8 hours. Through my experiments it seems clear that it doesn't have to do with the DVD/CD drive, because I can reproduce the problem with USB as well. I tried it again and it stopped if I check 'third party software' and it often stops after the partition table. With nomodeset I managed a full installation, but then I had no keyboard or mouse. I read a lot of errors about 'irq handler vector'. Does that mean anything? One installation worked but the the computer was incredibly slow,

---

### Post by LuJo on 2017-03-12
It works now. It took three weeks and it was three things. Nouveau graphic driver, LAN problem, and hardware in the sense that a BIOS update solved all three! BIOS helped fixed the LAN which enabled the download of the nvidia graphic drivers during the installation (with nomodeset). OpenSuse has an extra window during installation that warns about nouveau, and where you can reject or accept it, but it still didn't work for me, maybe because I had no internet. The 'wicked' internet programm from OpenSuse was a disaster for my board. So it looks like I will stay with Ubuntu for a while unless I get very bored, because I much prefer Gnome. Thanks for the suggestions.

---

### Post by mörgæs on 2017-03-12
Good, please mark the thread 'solved'.

---

