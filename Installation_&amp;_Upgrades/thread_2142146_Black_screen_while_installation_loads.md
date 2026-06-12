---
title: "Black screen while installation loads"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by Ussop on 2013-05-04
I just downloaded Desktop Ubuntu 13.04 32bit ISO, made bootable USB stick according to instructions on the site ([ubuntu.com]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")).
Booted my PC, selected boot device (USB stick with Ubuntu). Screen, w/ "Try Ubuntu", "Install Ubuntu", "Memory Test"
and some other options, loads. When I select "Try Ubuntu" (or Install) some lines of text scroll down and screen with
Ubuntu logo and some white/red dots cycling appears (on dark violet background). After some time dots stop cycling and
I get black screen (with 2 vertical white lines at the edges, but that may be my monitor), nothing happen after that.

I got 2 HDDs, on smaller one win7. Old Ubuntu 8.04 loade w/o any problems from DVD.
Burning DVDs is not an option in foreseeable future.


On side note, If someone can point me to where I can find some info on handling HDDs, that get "Failed S.M.A.R.T." at boot
screen, I would appreciate that. I'm just hoping to recover some important data. It is NOT related to above problem.

---

### Post by MAFoElffen on 2013-05-04
What video card do you have? Affects what to use for a boot param...

On USB Boot, are you using unetbootin? Affects how to edit the boot line...

Once you get the live image to boot, you could install "smartmontools" to test and queries smart statistic of a disk... but I can tell you, just because a disk fails smart with one utility, doesn't mean the disk is bad. I do work for a computer recycler and we test and recondition disks for sale. Sometimes you'll get a false error based on compatibility between disks and monitoring tools. Just because it fails with one utility, if you try with another, some might pass with flying colors. 

But for testing and repairing disks, I usually use low level disk tools on a bootable device. I usually use a low-level utility comparable to the disks I'm working on. I do a low-level format, verify and mark out any bad sectors. The I test. Once the sectors are marked out, as long as not excessive and depending where those bad sectors are located, it's then good to go. I then clear the smart status log. I have a 1TB drive in one of my test boxes that someone said was bad... that has ran almost constantly 24x7 for 3 years so far without problems. It does take a "long" time. If I have a stack of drives to do, I usually setup 5-6 systems so I can do 5-6 at a time.

---

### Post by Ussop on 2013-05-05
Thenk you for help.
I'm using GeForce GT 240 GS.

No, I used Universal USB Installer from pendrivelinux.com.

---

### Post by MAFoElffen on 2013-05-06
Look at Post 2 of my Graphics Resolution sticky (link in my sip line) for links to pertinent tutorials. I'm not sure about Universal USB Installer. If it's like unetbootin, when the first menu comes up, press the <Tab> key to get into an edit mode...

Okay. I found it on the Debian boards. The edit hotkey is the <Tab> key. When it goes into edit mode, arrow down to the line that starts with "linux"... Arrow over after where it says "quiet splash" and before it says "$vthandoff" and add the parameter "nomodeset". Press <Enter> to boot.

Once you install, after the reboot, then use my sticky for instructions on temporarily editing the grub menu to add the "nomodeset" again until you can boot and install nvidia drivers.

---

