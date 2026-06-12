---
title: "How should I edit GRUB to make this config work?"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by marx2k on 2006-12-01
I have installed Edgy on this box to dualboot with XP.
The system is booting from a SATA drive.  

I've edited GRUB to boot edgy fine. It's booting from /dev/sda7
XP should be on /dev/sda1

When I try to boot normally into XP, it shows NTKERNL Not Found CTRL+ALT+DEL ...

However, when I start the LiveCD and tell it to boot from the first hard drive, XP boots fine.

Can someone give me advice as to what numbers to put into the GRUB menu to have XP boot properly from the hard drive?



Here is fdisk -ul:
```

Disk /dev/hda: 13.6 GB, 13676544000 bytes
255 heads, 63 sectors/track, 1662 cylinders, total 26712000 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    26700029    13349983+   7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   240107489   120053713+   7  HPFS/NTFS

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sda2        40965750   625137344   292085797+   f  W95 Ext'd (LBA)
/dev/sda5        40965813   245762369   102398278+   7  HPFS/NTFS
/dev/sda6       450559053   625137344    87289146    7  HPFS/NTFS
/dev/sda7       245762433   266245244    10241406   83  Linux
/dev/sda8       266245308   447233534    90494113+  83  Linux
/dev/sda9       447233598   450558989     1662696   82  Linux swap / Solaris

```

I am booting Linux from /dev/sda7 and XP is on /dev/sda1

Here is how GRUB is set up:
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```

device.map looks like:
```

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda

```

Output of df -Th is:
```

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda7     ext3    9.7G  2.4G  6.8G  26% /
varrun       tmpfs    506M   96K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
procbususb   usbfs     10M  128K  9.9M   2% /proc/bus/usb
udev         tmpfs     10M  128K  9.9M   2% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
lrm          tmpfs    506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda8     ext3     85G  1.1G   80G   2% /home
/dev/hda1     ntfs     13G  2.4G   11G  19% /media/hda1
/dev/hdb1     ntfs    115G   95G   20G  83% /media/hdb1
/dev/sda1     ntfs     20G  7.9G   12G  41% /media/sda1
/dev/sda5     ntfs     98G  3.9G   94G   4% /media/sda5
/dev/sda6     ntfs     84G  6.1G   78G   8% /media/sda6

```

---

### Post by marx2k on 2006-12-01
One other question.. I also notice that giving 10G to '/' may run out at some point soon.  I'm wondering if it's possible to simply make another partition on another attached hard drive and extend / onto there? If so, how is it done?

---

### Post by Herman on 2006-12-01
>  I've edited GRUB to boot edgy fine. It's booting from /dev/sda7
XP should be on /dev/sda1 Well, it looks like your Grub considers your sda hard disk as disk number 1 since it boots Ubuntu up okay as (hd0,6). Logically then, it follows that your Windows install is probably seen as (hd0,0) by Grub. If you want to test that you could 'hash out' your existing Grub WIndows entry for now, and add a new grub menu entry under it and try to reboot to see if it works or not.


```
                                             
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root                                                
                                                  
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

# title        Microsoft Windows XP Professional
# root        (hd2,0)
# savedefault
# makeactive
# map        (hd0) (hd2)
# map        (hd2) (hd0)
# chainloader    +1

title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```Another way to find out what is going on and determine how Grub sees your hard disk is to try using Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") (CLI), (press 'c' from your Grub menu to get that), because that can give useful feedback that can help you. When you find out the correct information from CLI mode and boot with it, you can then edit your menu.lst with the same commands, so keep notes of what you do in CLI mode. The link already given should explain all about how to use CLI mode Grub.

---

### Post by marx2k on 2006-12-01
I will test it out in a moment and see if that works...

I noticed you also left out:
 map        (hd0) (hd2)
 map        (hd2) (hd0)

What is the function of the map identifier?

---

### Post by marx2k on 2006-12-01
Posting this from a properly booted XP. Right on! Thanks a bunch! I thought I tried 0,0 before and it didn't work. I guess I didn't try it after all!

---

### Post by Herman on 2006-12-01
>  I noticed you also left out:
 map        (hd0) (hd2)
 map        (hd2) (hd0)

What is the function of the map identifier? The pair of map commands is supposed to be for tricking Windows into thinking it is on a first hard disk when really it is on a second, third or fourth hard disk. Windows likes to think it is first on a first hard disk. 
Well, that's the most popular non-technical explanation I have read.  Probably there is a more accurate technical explanation. I'll keep my eyes open for one.

If your 'sda' is (hd0) to grub, then you shouldn't need the pair of 'map' commands, so I left them out.

:D

---

### Post by Herman on 2006-12-01
> Posting this from a properly booted XP. Right on! Thanks a bunch! I thought I tried 0,0 before and it didn't work. I guess I didn't try it after all! :D Great work! (You must have posted just as I replied  to your earlier post). Well done!, and thanks for the feedback too, I feel happy too when things are fixed successfully! :D

---

### Post by louieb on 2006-12-01
> **marx2k said:**
> One other question.. I also notice that giving 10G to '/' may run out at some point soon.  I'm wondering if it's possible to simply make another partition on another attached hard drive and extend / onto there? If so, how is it done?
No problem unless you plan on downloading and installing every program under the sun.  Large distributions like Fedora or Suse take about 7 gig for a full install. 
 But to answer your question. If you had planed ahead and created an LVM volume on the partition then you could easily add more space from another partition or hard drive. But as it stands now adding space to that partition can be done but it ain't easy.

---

