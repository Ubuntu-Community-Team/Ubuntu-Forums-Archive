---
title: "Installing with a windows 8 laptop"
date: 2014-01-27
forum: Installation &amp; Upgrades
---

### Post by Rory_OBrien on 2014-01-27
Hey everyone!  Just a heads up I am new to Linux (or at least installing) so please bare with me.  I'll keep this to the point.  I have a Windows 8 laptop right now and need linux on it for work.  I woud normal just follow a guide on line but I wanted some real person feed back first.  My laptop has 2 hard drives.  One 32gb flash drive with windows 8 on it for a quick boot up.  The other is for all the other junk.  I want to put ubuntu (maybe a different flavor) on the 500gb disk drive.  I guess my question is what do I have to do differently than normal becuase I am booting off 2 seperate drives?  And what program should lets me choose the OS right on boot up?  Any feed back woud be so much help.  I am pretty scared to start messing around with my computer.  Thanks!

---

### Post by fantab on 2014-01-27
What mode are you booting in, UEFI or BIOS. If Windows 8 came pre-installed with the lappie then the good chances are that you have UEFI. 
To confirm boot with Ubuntu DVD/USB and "Try Ubuntu without Installing". Open Terminal [Ctrl+Alt+T], run the following commands and post their output here:
```
sudo parted -l
sudo fdisk -l
```

Also tell us what Graphics Card do you have on board.

It will be good idea to go through this Wiki: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Rory_OBrien on 2014-01-28
I think its UEFI.  I have seen that term being used a bit.  the laptop had win8 preinstalled too.  I booted off my USB drive last night and it worked great!  I just need to know how to fully install it on that 500gb HDD.  I have 2 graphic cards the intel 4000 and the and an AMD 7600M series (forget the exact one.)  Hope this helps!  Thanks.

---

### Post by fantab on 2014-01-29
Good. We still need to see the output of those above posted commands.

---

