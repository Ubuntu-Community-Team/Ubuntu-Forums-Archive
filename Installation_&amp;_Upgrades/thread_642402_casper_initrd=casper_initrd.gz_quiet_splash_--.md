---
title: "casper initrd=/casper/ initrd.gz quiet splash --|"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by LittleTony on 2007-12-16
I got these 2 CD:
 "ubuntu, 2007, Bootalbe Installation CD" and 
"freespire, The freedom of choice, Bootable Installation CD"

I have this AMD KT133/KT133A with Win2000(looping off and on again at boot[no booting])

I want to install ubuntu whether destroying Win2000 or not.
I tried booting up with the ubuntu-Bootable, and got to a menu with 5 options:
Start or Install, Start in Safe Graphics, Install w/driver update, Check CD, MemTest, boot from HD
"Help" works.  And, Check-CD and Me-Test also work.

Start and Install w/driver update do not work; they go into "Installing kernel", progression bar,
also a flashing message saying: 
Boot options: casper initrd=/casper/ initrd.gz quiet splash --|
 and ends up 4 minutes later on a blank screen w/top-left blinking indicator and CD-activity-light on.

I tried to boot out of the freespire cd, and got:
ISOLINUX 3.11 Debian-2007-03-12 Copyright (C) 1994-2005 H Peter Amvin
-Loading..
FreeSpire Debian Linux case powered by ubuntu 
...
and then crash to:

  [  53.584657] Out of memory: kill process 2819 (tar) score 105 or a child
  [  53.584657] Killed process 2819 (tar)
and previous 2 lines again, left aligned though, and
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3r1cnr1) Built-in shell (ash)
Enter 'help' for a list of built-in commands, and
/bin/sh: can’t access tty; job control turned off 

I can see dev lib bin sbin... and other directories but 
that is about it.

Summary: I cannot install ubuntu in this computer.
I cannot understand these messages 
"(tar) score 105 or a child"  and  "can't access tty; job control turnerd off"
I cannot figure out how to modify some CD-batch file, in case that that would be an option to me.

Could you help me please?
Thank you for your attention

---

