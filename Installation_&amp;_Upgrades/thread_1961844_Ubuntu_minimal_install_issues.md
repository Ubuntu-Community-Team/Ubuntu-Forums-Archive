---
title: "Ubuntu minimal install issues"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by Mactownes on 2012-04-19
Alright, so the other day I decided to install Ubuntu minimal (found at [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)), as the only flash drive I have is 500 MB and I can't fit anything but Ubuntu minimal on it. Before you say "Try using alternate" I totally would, but I can't fit it on my current flash drive and I cannot obtain a larger one, nor can I obtain CDs to burn it to.

So anyways, I booted from the USB and did the installation. It gets to the end when suddenly it says "Cannot install grub". I went back and thought "Hmm... maybe I should try using LILO?" so I went back to the installation menu and clicked on "Install LILO to a hard drive disk". I went into the option and it asked me whether I wanted to install it to the master boot record or to the new Ubuntu partition. One important thing to note is that as I was booting from a USB drive, the USB drive was labeled as "/dev/sda". This means that the internal drive was labeled as "/dev/sdb". When I went to install GRUB, at the point where it failed the thing it said it was doing below the progress bar was "grub-install /dev/sda". This kindof worries me, as it seems it was trying to install it to the flash drive. When I went into the LILO option, it said did I want to install it to the master boot record of "/dev/sdb" or to the Ubuntu partition on "/dev/sdb". I have tried both and neither have worked, I boot it up after successfully installing LILO and finishing the installation and with both options for LILO it says:
```
LILO 23.2 Loading Linux.......................................................................................
BIOS data check successful
[     1.007449] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[     1.007553] Pid: 1, comm: swapper Not tainted 3.0.0-17-generic #30-Ubuntu
[     1.007652] Call Trace:

```And then after that a lot of stuff, if you really need that to be able to help me just ask and I guess I can type it out.

So basically what I need help with is either how can I get GRUB to install, or get LILO to work?

And yeah should it be saying "grub-install /dev/sda", while all the other options including LILO say it's installing to /dev/sdb?

Thanks :cry:

EDIT: the machine is a Dell Inspiron 1720, 32-bit, and the connection I'm using is over ethernet.

EDIT: it was solved by a friend of mine, thank GOD. What you have to do is when you get to the stage where GRUB asks whether or not to install to the master boot record, say NO, and it takes you to a new screen. In the text box that appears type ¨/dev/sdb¨.

---

### Post by mörgæs on 2012-04-21
Good, please mark the thread 'solved' using 'thread tools'.

---

