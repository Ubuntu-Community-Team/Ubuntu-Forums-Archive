---
title: "[SOLVED] Grub problem on Feisty install"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by nowhere@cox.net on 2007-09-19
I have a problem that has been seen in the past. I have a SATA drive, with windows XP and a IDE drive with a partition for Ubuntu. Boot order has SATA drive first but it seems that grub install STILL considers the IDE drive first and installed there so my machine boots directly to windows with no grub menu. So grub is installed on (hd0,0) by default from the installer if I tell it to got to MBR yah? 

Unfortunately I don't know much about grub. Reading the posts here about the problem gives me enough insight to know this is my problem but I don't know the mechanics of how grub works so I would LOVE a bit of education here. 

Booting from the Live CD, fdisk shows my two drives /dev/sda and /dev/hdd (this one with the partitions it set up for Ubuntu) and another hd something which is the remaining space on the IDE drive left for windows, which I plan to mount in Ubuntu as a shared drive between the two op sys. 

How does the hdd's and sda's relate to the (hd0,0)'s and (hd1,0)'s in grub? Is the 0 and 1 the boot order as grub sees it? 

How do I tell grub to install on the MBR of the drive that actually has the MBR? Boot live CD, sudo grub, find /boot/grub/stage1 <- gonna point to the hd0..., root(dont know what to put here), setup(dont know what to put here).

Do I have to delete grub from the other drive somehow?  

After this is fixed and when I upgrade is it going to all get undone?

Any answers will be greatly appreciated!
Eric

---

### Post by confused57 on 2007-09-19
Here's is about the best guide I've seen on grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

If you're able to boot first to your IDE drive with Ubuntu, you could add an entry to boot Windows from grub.

If you're unable to boot first to your IDE drive, you can mount your Ubuntu's root partition with the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
there are instructions in this link for opening your menu.lst to determine how grub recognizes your hard drive order...If your Ubuntu drive is recognized as (hd0), there may already be an entry to boot Windows.  You would need to post your menu.lst here before anyone could give you correct advice on which drive's mbr you need to install grub.  If your Ubuntu drive is recognized as (hd0) by grub, you would have problems by trying to install grub's IPL to your Windows drive's mbr.
You might also want to post your device.map:
```
gedit /boot/grub/device.map
```

You want grub installed to a drive's mbr, which is designated as (hd0), (hd1), (hd2), etc...(hd0,0) is the first partition on the first hard drive and you don't want to install grub on a partition, the only time you would install grub to the root partition is if you're booting multiple distros.

---

### Post by nowhere@cox.net on 2007-09-20
Thanks for the reply. Wasn't able to get on the machine last couple night but I am now. I booted with the Live CD and here is the fdisk and grub info.  

ubuntu@ubuntu:/mnt/boot/grub$ more device.map
(hd0)   /dev/hdd
(hd1)   /dev/sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        4997    40138371    7  HPFS/NTFS
/dev/hdd2   *        4998        9529    36403290   83  Linux
/dev/hdd3            9530        9729     1606500    5  Extended
/dev/hdd5            9530        9729     1606468+  82  Linux swap / Solaris


grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,1)
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd1) (hd1)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

menu.lst looks like this
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=87579504-f3bf-4627-85a
4-fc9c8521f9cc ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

(Which seems correct to me...)

Now that I have done this, I DO get the grub menu with all the correct option (Ubuntu, recovery, Windows and others). But when I select Ubuntu I get a no such partition error. 

Any clues?

Thanks a ton for the help so far!
Eric

---

### Post by meierfra on 2007-09-21
In menu.lst change

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,1)

 to

title Ubuntu, kernel 2.6.20-15-generic
root (hd[COLOR="Red"]1[/COLOR],1)


(Since your are booting from sda,  now also ubuntu considers sda to be the  first drive.)

---

### Post by confused57 on 2007-09-21
meierfra is right that you need to change Ubuntu's root to (hd1,1), if you're booting first to your other drive...you can temporarily change this by highlighting your Ubuntu entry in your grub boot menu, press "e", then highlight the line with root, press "e" again, change root from (hd0,1) to (hd1,1), press "enter", then "b" to boot...if it works, you can make it permanent in your /boot/grub/menu.lst.  Report back if it works & I or someone else can give you instructions for making it permanent and adding a Windows entry, if need be.

---

### Post by maybeway36 on 2007-09-21
No GRUB menu? It's probably not booting GRUB. Try making a seperate /boot partiton on the IDE drive when you install Ubuntu. (It does not need to be very big, 128MB should be more than enough.)

---

