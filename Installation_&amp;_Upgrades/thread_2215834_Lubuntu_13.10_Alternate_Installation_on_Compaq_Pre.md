---
title: "Lubuntu 13.10 Alternate Installation on Compaq Presario 2500 - The Adventure"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by maccoutinho on 2014-04-08
Hi guys,

So I'm trying to install Lubuntu 13.10 Alternate Installation on aCompaq Presario 2500.
I've used a CD-RW to burn the iso from my HD and when verifying it Nero prompted quite some errors.
Still I popped it on my god forsaken Presario 2500 and he managed to read it, load all the modules and configure my ethernet connection so I thought I was set.
Sadly it seems the installation has frozen on a blue screen with a command prompt on the bottom (I tried pushing a few commands in but nothing happens).
The laptop seems to be reading from the disk but not from the cd.
What do you guys think is going on? 
Is the installation actually taking place?

Thanks in advance for the help!

---

### Post by maccoutinho on 2014-04-08
Wasn't even aware this laptop could boot from usb, gonna give that a go and see if it installs.

---

### Post by ajgreeny on 2014-04-08
If Nero showed some errors there is honestly no point trying to install with that CD.

Did you check the iso file you downloaded against the published md5sum list at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") to make sure there are no download errors there?  If not do so now and download again if there are discrepancies showing.  Always burn the CD at the slowest speed available.

---

### Post by maccoutinho on 2014-04-08
I'm trying to install from usb and so far so good. On my first try I was getting a "debootstrap" error, don't know why, but it seems the installer is managing to install the base system this time around so lets keep our fingers crossed!

---

### Post by maccoutinho on 2014-04-09
The system is up and running. Still I'm sad to realize that even for  Lubuntu my pitiful Compaq Presario 2500 seems to have lower than  required specs.

---

### Post by sudodus on 2014-04-09
Please tell us the specs of your Presario, particularly the RAM size is important for the performance.

- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Pentium 4 is OK. To make the computer useful for everyday browsing (the internet), you should have at least 512 MB RAM.

See this link for more details [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by maccoutinho on 2014-05-12
[http://www.cnet.com/products/compaq-presario-2500-15-mobile-pentium-4-win-xp-home-256-mb-ram-40-gb-hdd-series/specs/](http://www.cnet.com/products/compaq-presario-2500-15-mobile-pentium-4-win-xp-home-256-mb-ram-40-gb-hdd-series/specs/)

These are the specs but I bought 2x512mb ram which I'm going to replace.

At this moment it only has 2x256mb.

I've been paying closer attention to the way the laptop works and I've noticed that it runs completely smoothly at first and only after it starts heating up it begins to hang.
[U][B]
So I flipped the laptop and, alas, it seems only the fan connected to the heat sink is working, there are two secondary fans that remain still no matter how hot the laptop gets.[/B][/U]

** Do I have to install some specific fan control drivers in order to get the two additional fans working?**

This should solve the problem, I think.

---

### Post by sudodus on 2014-05-12
I think your observations are correct, but I don't know how to find out if the fan problem is a hardware or software problem. My only tip is to try a flavour or re-spin based on Ubuntu 12.04 LTS, that might work better with old hardware.

- Xubuntu 12.04 LTS
- Bento, Bodhi or LXLE

I hope ***someone with more experience of temperature control and fans*** will chip in and help you :-)

---

