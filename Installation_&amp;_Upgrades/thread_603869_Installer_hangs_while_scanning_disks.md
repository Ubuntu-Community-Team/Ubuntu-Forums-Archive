---
title: "Installer hangs while scanning disks"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by Kizlum on 2007-11-05
Hello everybody.
I try to install Ubuntu Gutsy on my desktop. I've already installed it on this computer, but I've installed Gentoo after, then finally, I prefer Ubuntu. So, I try to install Gutsy. The installer hangs on the disks exam at 46%, so, I think it's an hard drive partition table problem, but Gentoo's livecd hasn't any problem with hard drive.
Here's the partman log file:
> /bin/partman: *******************************************************
/lib/partman/init.d/01unsupported: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
prted_server: Opening infifoarted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/bin/partman: *******************************************************
/lib/partman/init.d/01unsupported: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo

So, the installation can't finish. :(
Can you help me to solve this problem ?

I have a Maxtor hard drive with an Intel Core 2 Duo CPU with JMicron chipset.

(Sorry for my bad English, I'm French and not good at English !)

---

