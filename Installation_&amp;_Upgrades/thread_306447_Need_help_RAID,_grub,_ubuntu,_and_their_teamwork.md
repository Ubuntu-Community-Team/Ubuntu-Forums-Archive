---
title: "Need help RAID, grub, ubuntu, and their teamwork"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by bum99 on 2006-11-25
Heres my problem:
    I have 2 hard drives in RAID 0 with windows installed
    a Ubuntu installation on a seperate IDE hard drive
    grub doesn't even show when I boot up
    and in the grub configurations, windows isn't on the list.

I first tried to install Ubuntu on the RAID array but the partition editors wont recognise it even when I followed a few tutorials I found. So I went out and got another hard drive, installed it and put Ubuntu on. After rebooting and ejecting the CD, I was eager to be greeted by the familiar grub menu but the good ol windows load bar came up. When I got into windows I grabbed the EXT2 ifs program and looked at the grub configurations and saw ubuntu on the list but no windows (I'm figuring because its on the RAID array and wasnt recognised). ](*,) I really want Ubuntu goodness on this computer so any help would be really appreciated... or am I just screwed.

---

### Post by Spano on 2006-11-25
You may be in luck.  If the RAID drives are SATA and you say your new drive is IDE then you should be able to go into the BIOS and
change the IDE drive to the first device in the boot order.
Then you add Windows to menu.lst with somthing like this:
```
title Other operating systems:

title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
```

The map map bit is to fool Windows into thinking it's on the first hard drive.

See this page - section 4.2.6
[http://www.gnu.org/software/grub/man...OS_002fWindows](http://www.gnu.org/software/grub/man...OS_002fWindows)

---

### Post by bum99 on 2006-11-25
Sweet, I'll try it

Edit: It works like a charm, you are awesome Spano! :D

---

### Post by Spano on 2006-11-25
Glad to hear that worked for you.

---

