---
title: "Dual boot from different HD"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by ddevore on 2007-01-12
I have made the switch to Ubuntu from Windowz and am really liking it. The problem is I am a gamer and like my games. I have installed UT but found that it has sound problems and crashes a lot. I would like to fix the problems but in the short term I would like to run a dual boot with windows but don't want to mess up my Ubuntu drive. I would like to install an extra HD and install Windowz on it for my games and run Ubuntu from the existing drive.

By my understanding Windowz will only run from hda so installing it on the extra drive I have in there now is not an option. Current setup is hda 160 GB pure Ubuntu hdb 250 GB not being used, planning on making it a backup and file storage drive, and can install Windowz on it. 

What I was thinking about is this. Swap the drives and install Windowz on the 250 (now hda). Boot to the Ubuntu desktop CD and install grub to the Windowz partition and set it up to go to my hdb for Ubuntu. 

Questions:
1. Is it possible to boot Ubuntu off hdb with grub installed on hda? 
2. Can I do this without messing up the currently installed grub on my current install. 
3. How do I install and configure grub to work this way. 
4. Is there a better way to do this? 

Side Question:
How do I fix this sound...Is there a better way to get sound from multiple applications than aoss? 

Thanks for any help. 
Dru

---

### Post by bulldog on 2007-01-12
Unplug hda [ubuntu] and install windows on the new hdd.
Add a windows entry to your menu.lst```
gksudo gedit /boot/grub/menu.lst
```
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

You can add your windows and other partitions in your fstab to let them mount when you use ubuntu,if you want.
Here's a tutorial how it's done,[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

