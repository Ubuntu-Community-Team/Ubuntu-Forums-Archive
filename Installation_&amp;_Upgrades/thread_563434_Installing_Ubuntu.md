---
title: "Installing Ubuntu"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by igggyc on 2007-09-30
Hi

Any help on this would be strongly appreciated.

I just bought my new Dell Inspiron 1720 laptop, with a 250 GB SATA hdd, flash cache module enabled, and HDD behaving as AHCI. I have made a prtition on my HDD, hence creating a 100GB partition on which I want to install Ubuntu.

Trying to install Ubuntu, 7.04. I have the correct distribution of it for my intel laptop.

Set my bios to boot off CD/DVD drive, it boots up fine.
I select the option of installing Ubuntu.

1 minute into the process, it hasn't begun installing, but gives me the following message:

[B]BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)[/B]

I must mention, I am completely new to Linux, I have no idea about command line promps, command lines, or any coding of any sort. The solutions out there all talk in a level of jargon that I don't understand. I need a simple explanation of how to fix this error and install Ubuntu. Btw, I have tried this with HDD behaving as ATA and AHCI. Always the same error.

Any help is appreciated!!!!

---

### Post by taurus on 2007-09-30
Where did you get that installing CD?  Did you burn it yourself?  If you did, how fast did you burn and before you burnt it, did you run the checksum of the .iso file first?

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by igggyc on 2007-09-30
Burnt the ISO myself, got it from the Ubuntu site...

---

### Post by taurus on 2007-09-30
How fast did you burn?  Try burning it at a slower speed like 4x and make sure you run WinMD5Sum first before you burn it to check the integrity of the .iso file.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by meonkeys on 2007-10-02
First try the "super safe install" options [listed here]("http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html").

Also see this post: [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

I'm trying to use a Dell Latitude D630 and it is a little tricky to get Ubuntu on there so far. I was able to get past what seemed to be DVD mounting/reading problems with the 7.04 LiveCD by adding "break=top irqpoll" to the boot options, then typing "modprobe piix" and then "exit" at the "(initramfs)" prompt. But I never could get graphics working, even using tips from [this post]("http://users.piuha.net/martti/comp/d630/index.html").

Now I'm trying the alternate 7.10 install CD. It seems to be working (although the display just screwed up). I'm hoping enough good stuff gets installed properly before I reboot and start working on the graphics using [Voland666]("http://ubuntuforums.org/member.php?u=326528")'s [advice]("http://ubuntuforums.org/showthread.php?t=494943").

> **igggyc said:**
> flash cache module enabled, and HDD behaving as AHCI.

Any idea if these advanced BIOS/hardware features need software (Linux) support? I have these in my BIOS too, but I have no idea what they are supposed to do.

What is a "flash cache"?

What is the AHCI setting do?

---

### Post by Fridididi on 2007-10-05
Try using the alternative text based install. It helped with my D830.

---

### Post by picopir8 on 2007-10-05
This sounds like the same error I had when installing Feisty on my work PC.  The video card was too new and was not recognized when attempting to boot.  After some searching around on these forums I found a work around but I probably could not find the solution again if I tried.   A much easier solution is to just download the alternate install CD.

---

### Post by meonkeys on 2007-10-11
The alternate install CD did work, thanks! Wifi required ndiswrapper, and I had to do funky stuff from [this post]("http://ubuntuforums.org/showthread.php?t=564581") to get sound to work.

This is a screaming fast laptop. I have the flash cache turned on, and I haven't seen any problems yet.

---

