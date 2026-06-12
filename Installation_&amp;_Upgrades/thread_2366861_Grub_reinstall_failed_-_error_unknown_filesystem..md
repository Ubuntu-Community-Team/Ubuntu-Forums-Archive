---
title: "Grub reinstall failed - error: unknown filesystem."
date: 2017-07-22
forum: Installation &amp; Upgrades
---

### Post by 74corvette on 2017-07-22
Hi I recently installed a second version of Ubuntu long side my main installation of Ubuntu 16.04 for testing purposes.  Once I was done with the second install I deleted that partition and tried to reinstall grub.  I have tried everything I can find to reinstall grub.  But no matter what I do I always get the error:

Reinstall the GRUB of sda5 into the MBR of sda
Installing [COLOR=#AA22FF]**for **[/COLOR]i386-pc platform.
grub-install: error: unknown filesystem.
grub-install /dev/sda: [COLOR=#AA22FF]exit [/COLOR]code of grub-install /dev/sda:1

This is my log from my latest attempt using boot-repair disc/tool.

[http://paste.ubuntu.com/25147073/](http://paste.ubuntu.com/25147073/)

I can boot into my ubuntu install if I use the supergrub2 boot disc and select the latest Linux kernel. so my install is still good but grub refuses to install.

Any help and ideas would be appreciated.

Thanks

---

### Post by yancek on 2017-07-22
You have Grub correctly installed to the MBR and the core.img file is present.  However there are no boot files shown in the output.  Can you mount sda5 from another device (flash drive, DVD) and check to see if you have a boot directory and see if there is a grub directory in it with the proper file as boot repair could not find it.  Various method of re-installing Grub are explained at the official Ubuntu documentation site below.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by 74corvette on 2017-07-23
I have purged and reinstalled grub many times and always get the same message when it is doing the os probing after install "[COLOR=#000000]grub-install: error: unknown filesystem"  

In my Linux partition sda5 the boot directories are there /boot, [/COLOR][COLOR=#333333][FONT=Ubuntu]/etc/grub.d & [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]/etc/default/grub.  All directories but [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]/etc/default/grub have files in them.  [/FONT][/COLOR][FONT=Ubuntu, Ubuntu Beta, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]/etc/default/grub is empty.  The date modified on those dates corresponds to to last time I installed grub so grub must be accessing the partition, but it always ends in unknown filesystem.

[/COLOR][/FONT]I will try it once again in case I missing something and let you know. Thanks

---

### Post by oldfred on 2017-07-23
I do not know why Boot-Repair has all the references to mdadm?
Did you turn on RAID in BIOS?
Was drive every configured for RAID?
Grub desktop usually does not install to RAID drives.

If RAID was turned on try this, never run on a RAID system:
 sudo dmraid -E -r /dev/sda 

And maybe run fsck on sda5:

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

---

### Post by 74corvette on 2017-07-23
Thanks for the suggestions, my computer is a older laptop with one hard drive and I have never installed a raid array.  I tried all of your suggestions but I keep on getting the same result at the end of the install [COLOR=#000000]"[/COLOR][COLOR=#000000][COLOR=#000000]grub-install: error: unknown filesystem" .  I have tried installing grub with boot-repair disc plus going through all the steps manually using the ubuntu live disc both give the same result.  Which makes sense as the commands look the same to me.

For some reason I keep getting a unknown filesystem error but when I boot into my ubuntu install with the supergrub disc everything works prefect. Except grub won't install.




[/COLOR][/COLOR]

---

