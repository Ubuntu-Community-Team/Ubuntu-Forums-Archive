---
title: "Neither 7.10 or 6.10 Install"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by RSaunders on 2008-01-05
I've been using Ubuntu 6.10  for a while on an old Mac.  With the demise of PowerPC support, I decided that for the upgrade to 7.10 I'd start with a new machine.

I have a simple system, Intel mobo and CPU, 1GB Ram. I'm using the on-board Graphics, LAN, and IDE controller.  On that one IDE channel I have a DVD burner (slave) and a 160 GB disk drive.  No floppy, No graphics card, nothing else in the box.

I started with the 7.10 desktop CD.  It doesn't boot.  I get some BusyBox screen that ends with (initramfs).  This happens with either "run and install" or "run and install safe graphics mode".  Though they work for some folks, I've never liked live CDs much.

Next I got the 7.10 alternate install CD.  It starts up and goes through "English" ... up to the point where it wants to find the CD drive.  It's unable to talk to "/dev/cdrom".  It claims there is no CD drive, even though it's running from the drive.  The installer suggests using ALT+F2 and seeing what the drive is called using "ls /dev".  That gives hundreds or TTY### and PTY### entries, that I don't have hardware for, and nothing I can recognize as either drive.

OK, maybe 7.10 isn't for me.  Next, I get a 6.10 desktop CD.  It boots up and works fine.  I get a Ubuntu desktop, and click on Install.  The installer runs, I tell it to use the whole disk drive because I want to avoid all the dual-boot problems I read in the forum.  The installer ends, unmounts everything, and ejects the CD.  When I boot, I get nothing.  After the BIOS splash screen, I get "No bootable devices, insert one and press any key".  No GRUB messages at all.

I decide that I really don't like live CDs, and I get the 6.10 alternate install CD.  I boots and works fine, I go through the whole process again.  Same exact result.  So, I get a Windows install CD, install Windows (thinking I have some MBR problem), reformat the whole drive.  Windows boots and runs fine.

Back goes the 6.10 alternate install CD.  Install Ubuntu for the 3rd time, use the whole disk and erase that darn Windows partition.  Install works fine, unmounts volumes and ejects CD.  Reboot.  "No bootable devices ..."  Argh.  Then I make a very interesting mistake.  I grab the Windows install CD by mistake.  I put it in the drive and reset.  I get a message that says "press any key to boot from CD".  Realizing my mistake, I am getting the right CD when the timer runs out.  I get GRUB.  This is where windows would be booting the hard disk because I didn't press a key, and it seems Ubuntu is booting.  While I'm considering the horror of needing a Windows install CD to boot linux, GRUB dies, error 25.

I've searched all through the forum, and the GRUB error 25 folks are all doing the complicated dual-boot thingy that I'm sure I want to avoid.  Frankly, I'm stumped as far as what to try next.

I've been through all the BIOS settings, I have the drive order set to Optical drive then hard drive.  I don't have anything else to put on the list anyway.  I tried setting the disk drive spin up delay from 0 to 5, that only makes it not boot more slowly.

Is my problem too simple?  What am I not doing?
Thanx in advance.

---

### Post by Partyboi2 on 2008-01-05
Have a look here
[http://users.bigpond.net.au/hermanzone/p15.htm#25](http://users.bigpond.net.au/hermanzone/p15.htm#25)

---

### Post by RSaunders on 2008-01-06
Partyboi2,

   An interesting link.  One line "make sure you use a good quality 80 conductor cable" got me thinking.  I was using a 40 conductor cable because it was not cable select, and a little longer.  I switched the drives to cable-select and tried another cable.  Now 7.10 installs and boots.  The bootstrap must not have error retry logic like the installer and Windows.  I was probably getting lots of soft disk read errors.

---

### Post by Partyboi2 on 2008-01-06
Herman's grub page is full of useful troubleshooting ideas, as well as great information on understanding grub. Always handy to have bookmarked. Glad you got your system up and going :)

---

