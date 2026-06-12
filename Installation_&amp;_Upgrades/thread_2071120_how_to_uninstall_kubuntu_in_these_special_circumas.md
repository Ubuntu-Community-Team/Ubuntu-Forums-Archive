---
title: "how to uninstall kubuntu in these special circumastances ?"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by eslam elbyaly on 2012-10-14
hi all , i had xp and kubuntu , then i tried to uninstall kubuntu incorrectly by deleting it's partition , so , i had the grub rescue prompt , 
- then , i used the boot-repair tool , and now i've got kubuntu again , but no xp anymore . 

- what i want now is , (uninstalling kubuntu completely , and install xp again , just xp ) .

- i've got a lot of problems now , i can not boot with my xp cd to install , neither my flash drive , and i had ubuntu cd , and it worked well 4 days ago  , but now it does not . 

- i am attaching a pic for my partition table before using the boot-repair tool . , if you could tell me in what partition kubuntu resides , c or d or e , because i really do not know , because it was installed incorrectly , not in a private partition for boot and a private one for swap , as the tradition way .

---

### Post by oldos2er on 2012-10-14
Kubuntu will be the ext4 partition.

You'll need to restore Windows' boot loader first; once you do that and boot into Windows, you can delete the ext4 partition or reformat it to NTFS.

---

### Post by eslam elbyaly on 2012-10-14
> **oldos2er said:**
> Kubuntu will be the ext4 partition.

You'll need to restore Windows' boot loader first; once you do that and boot into Windows, you can delete the ext4 partition or reformat it to NTFS.
thanks man for your reply , but 

- as i said before , that was the situation , i had xp and kubuntu then i deleted the kubuntu partition from xp , so i had no boot loader for windows , it was crashed . 

2- i know that ext4 is the kubuntu's partition , but as i also said before , that it was installed incorrectly , that ext4 is not a standalone partition , i think it is a part of another partition , it is inside a fat32 one , i think . 

3- how would i restore windows boot loader ? 

thanks in advance

---

### Post by ajgreeny on 2012-10-14
Your screenshot suggests you can boot to ubuntu.  Was that live or installed OS?

You seem to be saying that you can't boot to a live CD, nor the winXP install CD.  Are you sure that CD-ROM is first in the boot priority list in your BIOS?

---

### Post by eslam elbyaly on 2012-10-14
> **ajgreeny said:**
> Your screenshot suggests you can boot to ubuntu.  Was that live or installed OS?

You seem to be saying that you can't boot to a live CD, nor the winXP install CD.  Are you sure that CD-ROM is first in the boot priority list in your BIOS?
my screenshot was by a live cd (i think) , 

- cd has the priority to boot . 
- consider that as well , i can not boot even with my flash drive . 

and by the way , i tried to restore my windows boot loader by writing this :
sudo apt-get install syslinux

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

as written here : 
[http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/](http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/)

and now , unfortunately , i have nothing , no kubuntu anymore , no xp , no live cd can boot neither my flash drive . 

helllllllllllllpppppppppppp ?

---

### Post by bra|10n on 2012-10-14
Some questions;

1. Do you own a copy of WinXP installation disk?
2. Do you have a copy of GParted on disc?
3. How much personal/saved data is still on your windows partitions?

---

### Post by eslam elbyaly on 2012-10-14
> **bra|10n said:**
> Some questions;

1. Do you own a copy of WinXP installation disk?
2. Do you have a copy of GParted on disc?
3. How much personal/saved data is still on your windows partitions?
1- yes .
2- i've got ubuntu live cd and live usb , and the two or them do not boot anymore
 , i do not know why . 
3- hours ago , before the last step i did to restore windows boot loader , all my data
were alive . 

p.s : - gparted or disk utility or partition manager , all of these see my hard disk as one whole unit , they do not see it as partitions , just one unit . 

2- the usb and all of my cds are working very well on any other pc .

---

### Post by bra|10n on 2012-10-14
Well I fear that this situation is not going to be recoverable without a complete disk format...
**However you might wish to wait before rushing to format in case someone else here has a better solution.**
If you have no files or other data you want to save then IMO this is the best solution.

While you wait you might want to think about what disk layout would best suit what you want to do, e.g dual-boot with WinXP and Ubuntu/Kubuntu.

---

### Post by oldos2er on 2012-10-14
> **eslam elbyaly said:**
> thanks man for your reply , but 

- as i said before , that was the situation , i had xp and kubuntu then i deleted the kubuntu partition from xp , so i had no boot loader for windows , it was crashed . 

When I said Windows' boot loader, I mean the boot loader program used by Windows, not grub.

> **eslam elbyaly said:**
> 2- i know that ext4 is the kubuntu's partition , but as i also said before , that it was installed incorrectly , that ext4 is not a standalone partition , i think it is a part of another partition , it is inside a fat32 one , i think . 

Your ext4 partition is an extended logical partition. You can delete or format it independently from the other two logical partitions you have.


> **eslam elbyaly said:**
> 3- how would i restore windows boot loader ? 

thanks in advance

You'll need a working WinXP CD.

---

### Post by bra|10n on 2012-10-14
The instructions given by oldos2er are worth trying... 
They may save you a WinXp reinstall and preserve any existing data.

Though I would recommend just deleting the Ext4 partition (it's only 3 Gb).

---

### Post by eslam elbyaly on 2012-10-15
> **bra|10n said:**
> Well I fear that this situation is not going to be recoverable without a complete disk format...
**However you might wish to wait before rushing to format in case someone else here has a better solution.**
If you have no files or other data you want to save then IMO this is the best solution.

While you wait you might want to think about what disk layout would best suit what you want to do, e.g dual-boot with WinXP and Ubuntu/Kubuntu.
what is (IMO) ?

---

### Post by eslam elbyaly on 2012-10-15
i repeat ,
1- my xp cd is working very well on any other pc .
2- i do not mind to delete the ext4 partition , this is what i want , but what i mean is  , even when i 'am able to install xp , then i delete the ext partition , then my windows boot loader will crash , since this what i did at the first . 
thanks

---

### Post by bra|10n on 2012-10-15
> **bra|10n said:**
> Some questions;

1. Do you own a copy of WinXP installation disk?
2. Do you have a copy of GParted on disc?
3. How much personal/saved data is still on your windows partitions?

For an individual desperately requiring help you pose a lot of questions of your own, and yet fail to completely answer those asked of you.

---

### Post by eslam elbyaly on 2012-10-15
i think my laptop went to hell , 
i tried everything , 
- i tried hiren's cd , it does not boot , it just boots when i plug my hard disk out . 
- i tried ubuntu live cd and usb , it does not boot . 
- finally , i connected the hd with sata cable to another laptop , the other laptop can not see it at all , i can not log onto the hard disk . 

what should i do , help , please ?????

---

### Post by darkod on 2012-10-15
I think you should ask some friend that knows more about computers to help you. I tried helping in your other thread too, but it's almost impossible since you are asking too many questions about everything, so instead of solving the problem it just takes forever. You have to understand that we can only give you guidance, we can't make the choices or hit the buttons for you. You have to make some choices yourself.

How did you check that the hdd is not seen on another computer? In windows? Windows is very limited when reading disks with errors in the partition table. You can't rely on that.

The best is to use linux tools and testdisk for example.

Another thing is booting the laptop from a cd. Are you sure you have set it up correctly? The cd-rom needs to be before hdd, otherwise it will try booting from the hdd. You can also try the Boot Menu that most computers have, usually you have to press a key on boot like F12, but it might be a different key on your machine. Watch the message during boot.

It should be able to boot from cd in any case.

If you manage to boot from the ubuntu cd in live mode, you can still try saving the data. Otherwise, if you can boot the XP cd you can format the disk and install XP.

In the case if the hdd is really dead, there is not much we can do for you.

---

