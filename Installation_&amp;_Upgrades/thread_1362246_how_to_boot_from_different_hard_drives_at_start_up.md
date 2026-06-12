---
title: "how to boot from different hard drives at start up"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by jackel7 on 2009-12-22
I just installed ubuntu on one drive and windows 7 on another. I want to be able to choose which one to boot from at start up instead of going to the bios and changing the boot order. I have 2 sata drives and a asus p5q-em motherboard.

all relevant suggestions are welcomed.:confused:

Thanks

---

### Post by starcraft.man on 2009-12-22
Requires manual editing. The ideal way is in my opinion to boot the linux partition, and make that the primary drive. Then edit in a custom grub menu entry to point to the secondary drive. At boot up you then have linux, and under option to boot windows.

Are you using Karmic or an older Ubuntu version, there are different GRUB's and they edit menus differently.

This is the grub2 doc page. It's a bit overwhelming, if your lost that's fine, post back what version of ubuntu ya have and I'll make one for ya. Also please post back the result of:

```
sudo fdisk -l
```

If it's not clear which one is windows please indicate.

---

### Post by jackel7 on 2009-12-22
karmic the 9.10

---

### Post by oldfred on 2009-12-22
If it is Karmic is it an upgrade with grub legacy still or a new install with grub2. All grub2 requires to add the windows entry is 
update-grub

If it is the older grub you probably have to add a manual entry, but we woudl need to see your configuration. May be able to do it with just 
sudo fdisk -l   (el not 1 or eye)

---

### Post by jackel7 on 2009-12-22
A new install it I think it was upgraded when the updates were installed

---

### Post by starcraft.man on 2009-12-22
> **oldfred said:**
> If it is Karmic is it an upgrade with grub legacy still or a new install with grub2. All grub2 requires to add the windows entry is 
update-grub

If it is the older grub you probably have to add a manual entry, but we woudl need to see your configuration. May be able to do it with just 
sudo fdisk -l   (el not 1 or eye)

Really, I've found the OS detection lousy with grub2, like they messed it up! neither my vista nor xp partition detected right. I ended up making manual entries and it worked. I could be an exception. To jackel do post if it's upgrade/not and output of the command (paste in a reply) we both gave in a terminal (Applications > Accessories > Terminal).

So to be clear, open the terminal, copy/paste next command command :

```
sudo fdisk -l
```

Whatever is returned in terminal, copy it all and paste in a reply. Please wrap it in code tags (the # button on reply editor).

---

### Post by jackel7 on 2009-12-22
sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9616e542

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01000100

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

---

### Post by jackel7 on 2009-12-23
sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9616e542

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01000100

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS```
[CODE]
```[/CODE]

---

### Post by oldfred on 2009-12-23
I have had good luck with grub2 finding other operating systems, much better that old grub, but not perfect.

If the update-grub does not work we have to add and entry to 40_custom and then run update grub to write that new entry into grub.cfg, Change the red entry to your uuid. - to see uuid's for sdb1 run 

sudo blkid
gksudo gedit /etc/grub.d/40_custom
sudo update-grub

menuentry "Windows " {
       insmod ntfs
       set root=(hd1,1)
       search --no-floppy --fs-uuid --set [COLOR=Red]EC0CEE940CEE595A[/COLOR]
       drivemap -s (hd1) (hd0)
       chainloader +1
}

---

### Post by poosietgp on 2009-12-23
if you are using grub2 just do a...
```
sudo update-grub
```
it will auto-detect OSes installed on any disk then input...
```
gksudo gedit /etc/default/grub
```
and edit this line...
```
#GRUB_DEFAULT=0
``` to ```
GRUB_DEFAULT=n
```
n = the OS detected by update-grub. 
NOTE: the value of 0 here means the first OS detected by grub and a value of 1 here means the second OS detected by grub.
for more information regarding grub2 specifics you can consult this thread.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jackel7 on 2009-12-23
> **oldfred said:**
> I have had good luck with grub2 finding other operating systems, much better that old grub, but not perfect.

If the update-grub does not work we have to add and entry to 40_custom and then run update grub to write that new entry into grub.cfg, Change the red entry to your uuid. - to see uuid's for sdb1 run 

sudo blkid
gksudo gedit /etc/grub.d/40_custom
sudo update-grub

menuentry "Windows " {
       insmod ntfs
       set root=(hd1,1)
       search --no-floppy --fs-uuid --set [COLOR=Red]EC0CEE940CEE595A[/COLOR]
       drivemap -s (hd1) (hd0)
       chainloader +1
}

Thanks this did it :)

---

