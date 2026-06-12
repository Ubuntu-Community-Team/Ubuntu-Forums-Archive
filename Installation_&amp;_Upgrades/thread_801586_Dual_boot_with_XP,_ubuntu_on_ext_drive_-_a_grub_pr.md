---
title: "Dual boot with XP, ubuntu on ext drive - a grub problem?"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by kdfox on 2008-05-20
So I installed ubuntu 8.04 on an external USB drive (so that it could have all the space i wanted for it etc), i chose the guided partitioning and clicked "use entire drive", this, somehow, hosed the mbr on my internal drive which is home to my main, xp, installation such that i could not get to eiter os (grub error 21 before grub ever even came up).  after downloading a freedos live cd and doing fdisk /mbr to get my mbr back, i cleared the ubuntu disk as best i could and reinstalled, this time choosing the guided partitioning as before but chose to go in to "advanced" and put grub onto the external drive as well.  i changed the boot order so that i could boot off the external drive and grub came up just fine, except i still get the grub error 21 when i try to go into any of the linux options listed and the windows option gives me the words "starting up" followed by absolutely nothing.  so at the moment i have reverted the boot order to just go straight to xp, just so that i can figure out whats going on.

so how do i get to the following configuration:
xp on internal drive
ubuntu on external drive
grub operating the way its supposed to

this last one seems to be the real problem

thanks in advance!

kevin fox

---

### Post by Pumalite on 2008-05-20
Restore your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Reinstall. This time, in step 8 go to Advanced Tab and change (hd0) for /dev/xxx; where xxx is your external drive. You can find this out in the Terminal with:
sudo fdisk -l
To be even surer; disconnect your internal drive during installation if this is a Desktop.

---

### Post by kdfox on 2008-05-20
> **Pumalite said:**
> Restore your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Reinstall. This time, in step 8 go to Advanced Tab and change (hd0) for /dev/xxx; where xxx is your external drive. You can find this out in the Terminal with:
sudo fdisk -l

so i should install grub onto the same drive as my ubuntu install?  i think thats how i have it now . . .

---

### Post by Pumalite on 2008-05-20
No, I don't think so. I think Grub got installed half in the external drive and half in the internal drive. Can you boot Windows without the external being connected?

---

### Post by kdfox on 2008-05-20
> **Pumalite said:**
> No, I don't think so. I think Grub got installed half in the external drive and half in the internal drive. Can you boot Windows without the external being connected?

yes.  in fact, when i set the bios to boot from the internal first, the system goes directly into windows without a peep from grub, but when the bios is set to boot 1. usb 2. first hard disk it goes into grub and then can't go anywhere from there

---

### Post by Pumalite on 2008-05-20
Boot your Live CD and with your external connected, post from the Terminal:
sudo fdisk -l

---

### Post by kdfox on 2008-05-20
> **Pumalite said:**
> Boot your Live CD and with your external connected, post from the Terminal:
sudo fdisk -l


here it is: 

> Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7efd7ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       14589   117145980    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9447    75882996   83  Linux
/dev/sdc2            9448        9729     2265165    5  Extended
/dev/sdc5            9448        9729     2265133+  82  Linux swap / Solaris


---

### Post by kdfox on 2008-05-20
is that output what you were looking for?

---

### Post by kdfox on 2008-05-20
hello?

---

### Post by confused57 on 2008-05-20
If you're getting a grub boot menu when you boot first to your external drive, select the first Ubuntu entry, press "e", select the line with root, press "e" again, change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot...leave the value for y as it is shown.  Report back if this works, this change is temporary, but can be made permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by kdfox on 2008-05-21
> **confused57 said:**
> If you're getting a grub boot menu when you boot first to your external drive, select the first Ubuntu entry, press "e", select the line with root, press "e" again, change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot...leave the value for y as it is shown.  Report back if this works, this change is temporary, but can be made permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```

thanks, i will try this when i get home from work this afternoon.

---

### Post by kdfox on 2008-05-21
it worked!  thank you very much (both of you).  one last thing - can i do a similar thing in grub to be able to get windows to boot from it?  it comes up as a choice in grub but then goes nowhere.  what should the command in grub (to boot xp) look like?

---

### Post by Pumalite on 2008-05-21
title Windows
root (hd0,0)
savedefault
chainload +1

Change root to whatever appropriate.

---

### Post by kdfox on 2008-05-21
> **Pumalite said:**
> title Windows
root (hd0,0)
savedefault
chainload +1

Change root to whatever appropriate.

How do i find "what is appropriate"?

---

### Post by Pumalite on 2008-05-21
It seems to be (hd0,1)

---

### Post by confused57 on 2008-05-21
> **kdfox said:**
> it worked!  thank you very much (both of you).  one last thing - can i do a similar thing in grub to be able to get windows to boot from it?  it comes up as a choice in grub but then goes nowhere.  what should the command in grub (to boot xp) look like?
Glad it worked...you'll also need to change the line with #groot to show (hd0,?).  If Windows is on the first partition of your internal hard drive, you'll probably need map lines:
```
title  Windows XP
root (hd1,0)
makeactive 
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
if Windows is on the 2nd partition, then root (hd1,1).

Try adding the above entry to the very end of your menu.lst...after the line ###END DEBIAN AUTOMATIC KERNELS LIST.

---

