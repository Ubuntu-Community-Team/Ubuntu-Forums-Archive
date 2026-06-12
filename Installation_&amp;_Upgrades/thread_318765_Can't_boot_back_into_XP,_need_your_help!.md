---
title: "Can't boot back into XP, need your help!"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by shiggs on 2006-12-14
Hey folks.  I recently installed and have been enjoying edgy.

However, I needed to run some windows apps so I rebooted and selected XP from the grub menu and got the missing hal.dll error.  

So after some searching here and google I figured it was a missing or incorrect  boot.ini file. So I booted from the windows CD, entered the repair console and  ran ```
e:\ bootcfg /rebuild
``` but I that failed, so I ran ```
e:\ chkdsk /R
```and then bootcfg again, but it still failed.

Now I should say that for some reason that escapes me at the moment, the windows install was not the cleanest to begin with.  The windows install was in F:\, but as you can see above when in the dos console windows show up in E:\.  I know I should have taken care of that or just installed linux on a seperate drive and changed my bios settings to dual boot, but that would have been to easy.

I at the point where the next thing I try could really screw stuff up and the last thing I want to be doing is fresh installs and a lot of data recovery, so I am here asking for some help.

This is whats going on the disks, all the OS's are installed on sdb*

```

:~$ sudo sfdisk -l

Disk /dev/sda: 24792 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+  24791   24792- 199141708+   7  HPFS/NTFS
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

Disk /dev/sdb: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          1    2610    2610   20964825    f  W95 Ext'd (LBA)
/dev/sdb2   *   2611   16845   14235  114342637+   7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sdb3      16846   19363    2518   20225835   83  Linux
/dev/sdb4      19364   19456      93     747022+  82  Linux swap / Solaris
/dev/sdb5          1+   2610    2610-  20964793+   7  HPFS/NTFS


```

The XP install I want to boot is located on sdb5


This is the relevant info from /boot/grub/menu.lst

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title           Windows XP Media Center Edition
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


```


Thanks in advance.

---

### Post by Sqwishy on 2006-12-14
Replace your windows thing in grub with this

```
title           Windows XP Media Center Edition
root            (hd1,1)
#savedefault
#makeactive
#map             (hd0) (hd1)
#map             (hd1) (hd0)
rootnoverify
chainloader     +1

```
maybe that'll work?

---

### Post by shiggs on 2006-12-14
thanks, but i got "error 11, invalid device string" or something like that.

---

### Post by bulldog on 2006-12-14
Which disk are you booting from?
Is it the sda or the sdb,this make a whole difference [why the mapping if you boot sdb?]

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors)

---

### Post by shiggs on 2006-12-14
> **bulldog said:**
> Which disk are you booting from?
Is it the sda or the sdb,this make a whole difference [why the mapping if you boot sdb?]

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors)
Yes I am booting from sdb

On sdb there are 2 ntfs partitions (1 w/ XP) a resierFS and a swap

I don't know why there is mapping, thats how I found it.

Thanks for the link, good summary there.

---

### Post by bulldog on 2006-12-14
The mapping has a purpose if you boot from sda and your windows is on sdb.
If windows is on the boot disk the mapping is useless.

Yes Herman is a real Guru on GRUB and booting,very knowledgeable.
He has several good info pages on his website.

---

### Post by shiggs on 2006-12-14
> **shiggs said:**
> Yes I am booting from sdb

On sdb there are 2 ntfs partitions (1 w/ XP) a resierFS and a swap

I don't know why there is mapping, thats how I found it.

Thanks for the link, good summary there.

for reference 

sda = maxtor (200gb)
sdb = samsung (160gb)


OK, i take that back, it looks like I am booting from sda (at least the disk order in the bios maxtor 1, samsung 2). Switching it around to samsung 1, i get no grub and a missing hal.dll error.   This is starting to make sense... and might explain why bootcfg failed.

So I guess grub is installed on sda (maxtor).  How do I check that? And what's the best way to go about fixing it.  

Maybe I just need to change my boot.ini file point to disk 1 instead of 0.

What a mess.

---

### Post by bulldog on 2006-12-14
To find out where GRUB is just try to boot from both hard disk,you should see it on one of those.
I understand that altering the boot.ini file can fix things.so give it a try.

---

### Post by shiggs on 2006-12-14
grub is definintely on the sda and the OS is on sdb, modding the boot.ini hasn't done anything (yet, but I am still trying)

---

