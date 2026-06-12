---
title: "installing hardy heron using its ISO"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by robert_ps88 on 2008-04-25
HI, I just wanted to share a very strange phenomenon.

i previously used ubuntu 7.10 everything works fine. i downloaded the 8.04 iso and burn it. then i backed up all my files in ubuntu and deleted its partiotion (thinking of starting all new)
but my CD drive is really bad on long time reading and it will totally stop at some point when i tried to install ubuntu.

so i was trying to find a way to install it diskless -ly 
it was no success


i extracted the iso to an empty partition then i reboot with the hardy disk inside my cd drive. STRANGELY, the CD sort of boot the partition with  the extracted iso in it and it actually run like LiveCD!!!
i can even eject the CD when i am on "liveCD" hardy and i can install hardy from this. its like diskless install. 
so the CD can like "kickstart" the partition with extracted ISO in it

WHAT i want to know is whether ubuntu is indeed built this way or is it just some good bugs.


anyway, the installation has some problems using this way.

this is my partitioning (what i wanted):

sda1:   windows C
sda2:   windows D
sda3:   ubuntu
sda4:   swap

as you all know a hdd can only be partition into 4 primary.
i was running the iso on the deleted swap partition.
the currently running partition cannot be edited in any way using this method thus we must sacrifice one partition. 
( i ahvent tested this thing on extended part)

so i found a way: i just extract the iso on system-less partition such as my D then run it then i do the partitioning for sda3 and 4 using gparted then install it. and clean up the extracted iso files later.

i do not know if this works on other computers so if anyone have same problem please contact me
thanks!!

i hope this can be useful for those who have WEAK CD DRIVE
and i would like very much to hear a reason for this phenomenon
a lot of things to be considered
e.g:
- can it kickstart USB/external HDD drive
- can an ubuntu CD kickstart different version of ubuntu "extracted iso partition"
- can it run extended partition.

---

### Post by Pumalite on 2008-04-25
Good.
There is another one:
[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

