---
title: "screwed up windows xp /ubuntu 7.04 dual boot"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by dachinster on 2007-05-01
ok so here is the deal. I am a Linux Noob, but an expert Windows user. Please take this into account when giving instructions

I have 3 SATA hard disks.
2 of the 3 disks are partitioned into two parts, meaning i have 4 partitions and 1 whole disk unpartitioned.

_Disk 1:_
XP is installed on C: Drive of the disk i assigned in my BIOS to be the 1st boot device
D: is where i store my documents

_Disk 2:_
Here i have a partition solely for downloads (E: )
F: is for backup

_ Disk 3:_
This is a brand new 320GB drive i bought. 
I decided to install Linux to this drive and i used the guided method utilizing the entire disk to format and install Linux.

The install goes well and it asks me to restart.
I restart, and it goes straight to Windows XP..............

I restart, go to my BIOS and change the first boot device to the Linux hdd.
Lo and behold, I get the OS choice menu and i choose the first option which is Ubuntu and it boots into Ubuntu with no problems. I use it and I am pleasantly surprised to see all of the stuff works without the breakage i read about elsewhere on the forums (most likely due to my using popular hardware)

Now, i reboot again and I want to use Windows....
I reach the OS choice menu, choose Windows XP and bam!

NTLDR missing. Press Ctrl Alt + Del to restart

I didn't panic. I simply went back into the BIOS and choose the disk with XP on it as my first boot device and when it restarts, it goes straight to XP again with no OS choice menu.

How do i fix this?
I realize the NTLDR error is occurring because when the drive is swapped around, the XP partition is no longer the C: drive and so windows complains.

How do i get the OS choice menu back?

---

### Post by confused57 on 2007-05-01
See this guide for editing your menu.lst & for a possible entry to boot Windows:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

If your Window's drive is recognized as (hd2), then an entry similar to this should work:
```
title              Windows XP
root               (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1
```

---

### Post by dachinster on 2007-05-02
i am actually amazed..
this worked!
only thing now is that i have no idea what some of those commands are! :P

i fiddled with the options u gave me and i customized the menu list as i wanted.


thanks!

---

### Post by AJ2005 on 2007-05-02
.

---

### Post by dachinster on 2007-05-02
ok. so everything works fine so far in ubuntu.
now, if i decided at some point in future to format my c: drive and re-install xp on the same partition.... will this screw up the stuff i just did to make it work?

will i have to rinse and repeat the above steps?

---

### Post by confused57 on 2007-05-02
> **dachinster said:**
> ok. so everything works fine so far in ubuntu.
now, if i decided at some point in future to format my c: drive and re-install xp on the same partition.... will this screw up the stuff i just did to make it work?

will i have to rinse and repeat the above steps?

You should be able to reinstall Windows & not have to change a thing in grub...before reinstalling, I'd set the drive you're reinstalling Windows on to be the first hard drive booted in bios...shouldn't be any problem at all.

---

