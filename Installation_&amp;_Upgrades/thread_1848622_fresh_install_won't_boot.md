---
title: "fresh install won't boot"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by 02darkRS on 2011-09-22
I set up as follows:
60GB OCZ SSD 
sda1 - ntfs (for future Windows 7 install)
sda2 - ext4 - /

I also have a 1TB HDD setup as follows:
sdb1 - apps
sdb2 - W7system files (stuff moved from ssd for space saving)
sdb3 - extended
 sdb5 - ext4 - /home
 sdb6 - ext4 - /tmp
 sdb7 - ext4 - /var
sdb4 - ntfs - data

PC boots through POST, shows OCZ drive, then goes to hardware monitor with a blank flashing _

I am in live cd now & see that ubuntu installed on sda2. the files & folders are there. i've gone through 3 separate threads describing using the terminal to find & or install grub.... it has not worked. i also read through the grub2 page linked in those threads & i'm lost.

I installed exactly as this shows: (i didn't use this but found it after & this is how i did it)
[http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)


trying
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

next try:
[https://help.ubuntu.com/community/Grub2#Methods_of_Reinstalling](https://help.ubuntu.com/community/Grub2#Methods_of_Reinstalling)

---

### Post by garvinrick4 on 2011-09-22
Open a terminal in your live CD and copy and paste these:
```
sudo mount /dev/sda2 /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sda
```
```
sudo umount /mnt
```
```
sudo reboot
```

---

### Post by garvinrick4 on 2011-09-22
If that does not work then problems need a boot_info_script to look at.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

If you need help running this just say so. Will be glad to help. Post to this thread if a problem
with my previous post. Either way let me know what is going on.

---

### Post by 02darkRS on 2011-09-22
thank you, this worked:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 I am up & running & assume I will need to do this again when I install windows7?

---

### Post by garvinrick4 on 2011-09-22
> **02darkRS said:**
> thank you, this worked:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 I am up & running & assume I will need to do this again when I install windows7?
Very Good and yes when you install Windows it will overwrite the grub2 (grub-pc) that is now
installed in your drives mbr (master boot record). Know real problem to replace grub now that
you have done it once, like riding a bike. Thanks for putting link in your post so others can see
and benefit.
Easier to install Windows first in dual boot for most.
Please mark as Solved in upper right of page under Tool Threads, enjoy your Ubuntu 02darkRS.

---

### Post by YesWeCan on 2011-09-23
Best to install grub tothe MBR of the 1TB HDD and boot using this drive. Leave the standard MBR boot code that Windows installs on the SSD. :)

---

### Post by 02darkRS on 2011-09-23
wouldn't that remove the benefit of using the ssd. boot time would be like a normal hdd system then right? 
 
I am still trying to understand the MBR. I get what it is & what it does but where does it go? I left 1MiB before sda1 as per gparted default. is this where grub went?

---

### Post by 02darkRS on 2011-09-23
> **garvinrick4 said:**
> Very Good and yes when you install Windows it will overwrite the grub2 (grub-pc) that is now
installed in your drives mbr (master boot record). Know real problem to replace grub now that
you have done it once, like riding a bike. Thanks for putting link in your post so others can see
and benefit.
Easier to install Windows first in dual boot for most.
Please mark as Solved in upper right of page under Tool Threads, enjoy your Ubuntu 02darkRS.
 
marked solved. forgot to do that last night. i already enjoy it. just need to find where things are & we'll be set. I always try to add links for later searches. I hate those threads where people get things figured out & leave it with no help for future searchers! thanks for your assistance!

---

### Post by YesWeCan on 2011-09-23
> **02darkRS said:**
> wouldn't that remove the benefit of using the ssd. boot time would be like a normal hdd system then right? 
 
I am still trying to understand the MBR. I get what it is & what it does but where does it go? I left 1MiB before sda1 as per gparted default. is this where grub went?
It won't make much difference to boot time - most of the boot time is the OS pulling itself together rather than the boot-loader.

The way it works is that the MBR is the first sector on the disk and normally contains universal boot code and a partition table. The boot code loads another boot code located in the boot sector of the "active" OS partition. This partition boot sector is normally called the "partition boot record" or PBR and has its own boot code that loads the boot-loader proper which resides inside the OS partition. This is how Windows works.

Ubuntu and Grub do not work this way for reasons I won't go in to unless you want to know. Instead, the universal code in the MBR is replaced with a Grub-only code and the Grub boot program is put in an "unused" gap between the MBR sector and the first partition instead of in the Ubuntu partition. This boot program, sometimes called core.img or the grub kernel, depends on other files inside the Ubuntu partition. So unlike the standard system, Grub is spread about the place.

Windows tries to be a good housekeeper by restoring the MBR boot code to the universal one whenever it notices it is "corrupted". This will stop Grub working. So it is prudent to not install Grub to the Windows drive. When you install Grub to the HDD it will load its kernel and then load its other files from the Ubuntu partition on the SSD and finally transfer control to the Ubuntu kernel that will do rest of the boot process out of the SSD.

---

### Post by 02darkRS on 2011-09-23
Does the MBR create itself? Is that what goes in the 1MiB in front of sda1? 
If not, with the partitioning scheme I created & the loading of / onto sda2, did I inadvertantly put grub onto the W7 Partition sda1? I did not read anywhere that I should have created a seperate MBR partition as sda1. It would seem like a waste of a partition to create one that small.

---

### Post by YesWeCan on 2011-09-23
> **02darkRS said:**
> Does the MBR create itself? Is that what goes in the 1MiB in front of sda1? 
If not, with the partitioning scheme I created & the loading of / onto sda2, did I inadvertantly put grub onto the W7 Partition sda1? I did not read anywhere that I should have created a seperate MBR partition as sda1. It would seem like a waste of a partition to create one that small.
This might help: [http://www.pixelbeat.org/docs/disk/](http://www.pixelbeat.org/docs/disk/)
The MBR is outside of the partitions and contains a partition table which is a table of contents of the locations and sizes and types of the primary partitions on the disk. When you format a disk the MBR is re-written. It may also contain a partition booting code that loads and runs the PBR of the partition with its boot flag set (also called the active partition) in the table.

The Grub boot code and the Grub kernel should normally be installed to the MBR area. This is what happens when you designate the install location as /dev/sdx. If you add a number to it, it will try to install to a partition but Grub is not meant to be used this way and it will not work reliably. The standard Ubuntu installer should not let people do this - it does cause problems sometimes.

---

### Post by 02darkRS on 2011-09-23
yes, that makes sense. now i just need to understand what I did incorrectly to my install which caused Grub to not load initially.

---

