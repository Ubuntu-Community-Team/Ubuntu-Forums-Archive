---
title: "Grub Error 17"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by cronk on 2008-06-23
I recently bought an HP laptop with Vista on it. 
I immediately loaded ubuntu on a 60 gb partition and resized my vista partition to 80 gigs. that was working fine until I burned vista recover discs and deleted the recovery partition so i could utilize that extra hd space for data. After doing this when i boot i get grub error 17. I figure this is due to the changes i've made to the partition table. 

my /boot/grub/menu.lst  as follows:

```
 

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=610f5f8c-70ba-4dda-acd8-4b903952f047 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=610f5f8c-70ba-4dda-acd8-4b903952f047 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=610f5f8c-70ba-4dda-acd8-4b903952f047 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=610f5f8c-70ba-4dda-acd8-4b903952f047 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS


```


Any help as to what to change to fix this or if I can reinstall grub and fix it that would be appreciated.

Thanks.

---

### Post by Pumalite on 2008-06-23
Post:
sudo fdisk -lu

---

### Post by cronk on 2008-06-23
Here is my fdisk -lu

```


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3284b64c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   200009249   100004593+   7  HPFS/NTFS
/dev/sda2       200009250   320014799    60002775   83  Linux
/dev/sda3       320014800   328015169     4000185   82  Linux swap / Solaris
/dev/sda4       328015872   625139711   148561920    f  W95 Ext'd (LBA)
/dev/sda5       328017920   625139711   148560896    7  HPFS/NTFS

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 3706 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      160649       80293+   0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdb2          160650    58605118    29222234+   b  W95 FAT32
ubuntu@ubuntu:~$ 



```

---

### Post by Pumalite on 2008-06-23
Edit menu.lst
Ubuntu's 'root' should be (hd0,1)

---

### Post by cronk on 2008-06-24
any idea how i can do that from the live cd ?

---

### Post by logos34 on 2008-06-24
click on root partition in nautilus file browser to mount it (usually does so at '/media/disk'), then:

gksudo gedit /media/disk/boot/grub/menu.lst

---

### Post by cronk on 2008-06-24
Thanks for all the help so far.

I've edited my menu.lst file and changed Ubuntu's root to (0,1)instead of (0,2) but I still get error 17 when booting.

Any suggestions?

---

### Post by sys_alpha on 2008-06-24
Error 17: could not mount selected partition.

i guess this happened because you deleted a partition.This happens if you do any change in the partition.

just change the root (hd2,0) entry to (hd1,0) in the menu.lst of /boot/grub by using live cd.

alternatively you can reinstall grub 
grub-install --root-directory="your linux root directory" again by using live cd.

---

### Post by Pumalite on 2008-06-24
Do you have Vista in the system? How did you partition?

---

### Post by cronk on 2008-06-24
Yes I still do have Vista on the system. 

I had a 300GB partition with Vista and a 20 GB HP recovery partition.

I repartitioned the 300 GB one so I had a 100 GB for vista and 60 for Linux. After doing this I deleted the HP recovery partition and then formed a new logical drive using the free space.

---

### Post by Pumalite on 2008-06-24
Did you do it with the Vista partitioner?

---

### Post by cronk on 2008-06-24
Yes, I used the disk management console in Windows to partition.

---

### Post by Pumalite on 2008-06-24
You did it well then. Your Linux is in sda2 (hd0,1). Have you changed the boot order of the drives? or, do you have a mix of SATA and IDE?

---

### Post by cronk on 2008-06-24
No I haven't changed to boot order of the drives. I've only got one SATA 320 gig HD.

---

### Post by muteXe on 2008-06-24
so if i was going to dual-boot ub with vista, you'd recommend using vista partitioner rather than the one the ubuntu installer uses?

---

### Post by Pumalite on 2008-06-24
If you are going to install in the same drive as Vista.

---

### Post by muteXe on 2008-06-24
Hmm cheers for that. New laptop came on friday and was going to install 8.04 on it in the same way i installed it on my xp desktop (ub installer).  Won't be doing it like that now.
(sorry for hijacking your thread Mr cronk :( )

---

### Post by Pumalite on 2008-06-24
> **cronk said:**
> No I haven't changed to boot order of the drives. I've only got one SATA 320 gig HD.
At the Grub menu; press 'e' to edit, press 'e' again and then try different numbers until you find what's the correct one. Then incorporate it to menu.lst. You could try reinstalling Grub too:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by cronk on 2008-06-24
I'm not sure if I'll be able to edit when I boot as I don't get the actual grub menu.

I get error 17 before the menu comes up, unless I can do it from the live cd menu when booting from that?

---

### Post by Pumalite on 2008-06-24
Do you get the message below: 'Press any key to continue...'?

---

### Post by cronk on 2008-06-24
No, no messsage after "Error 17"

---

### Post by logos34 on 2008-06-24
> **cronk said:**
> No, no messsage after "Error 17"

I think maybe we left out one thing: [rewrite grub to the mbr]("http://ubuntuforums.org/showthread.php?t=224351"), pointing to (hd0,1)...it's still pointing to (hd0,2), which is why no menu comes up

---

### Post by cronk on 2008-06-24
Thank you Pumalite and Logo34 for all your help. After making the necessary changes to the menu.lst and reinstalling grub to the mbr I was able to resolve my issue.

Great support as always from the Linux community.

---

