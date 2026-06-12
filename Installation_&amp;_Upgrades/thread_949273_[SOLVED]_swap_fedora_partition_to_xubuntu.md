---
title: "[SOLVED] swap fedora partition to xubuntu"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by michaelbenton1977 on 2008-10-16
Many moons ago I installed fedora core 5 on an old fujitsu laptop alongside a 98se windows partition.  I would like to swap the fedora partition for a more modern distro like xubuntu.  
I ran the CD first and checked out the partitions and ran a memcheck to validate what I am working with as it has been a while since working with this system.
I found 192mb memory with 40g HD, no errors.

/dev/sda1 is fat32 with about 20g part and only 7g used and boot, lba as the flags listed.

/dev/sda2 is ext3 and labeled "/boot" with 102m part and only 13m used and no flags listed.

/dev/sda3 is unknown with nearly 18g part and blanks for space used and unused but with an lvm flag.

I'm not sure how to approach the task of swapping OSes.
I'm not certain if /dev/sda3 is my fedora part, would someone please identify the parts for me?  Is the /dev/sda2 the mbr thus logically labeled "/boot"?


I see GParted (GUI) has an option to "format to" a particular part and then lists filesystems including one called "linux-swap"
would I format the fedora part with this filesystem prior to installing the xubuntu OS?

I have many questions, I hope I am not too wordy.


ThANx ;~]

---

### Post by Elfy on 2008-10-16
Boot with the livecd and run ```
sudo fdisk -l
``` from a terminal, not sure which menu it is in for xubuntu.

You'll need 2 partitions - one for swap one for /

There is a partition editor in a menu (I think) which you can use to resize and create partitions.

Get the output to the command and we can help you from there.

---

### Post by michaelbenton1977 on 2008-10-16
> **forestpixie said:**
> Boot with the livecd and run ```
sudo fdisk -l
``` from a terminal, not sure which menu it is in for xubuntu.

You'll need 2 partitions - one for swap one for /

There is a partition editor in a menu (I think) which you can use to resize and create partitions.

Get the output to the command and we can help you from there.


Here is the output for the fdisk list:
"Disk /dev/sda:  40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bcb08

.Device Boot..Start..End........Blocks...ID..System
/dev/sda1..*...... 1 2550 20482843+.. c. W95 FAT32 (LBA)
/dev/sda2.... 2551 2563.... 104422+ 83. Linux
/dev/sda3.... 2564 4864 18482782+ 8e. Linux LVM"

The partition editor in xubuntu is GParted in the System option under Applications.  I have explored the program a little so I am familiar with the Resize option.

Again my objective is to keep the Win98 part intact if possible.
What next?

ThANx

---

### Post by Elfy on 2008-10-16
Delete sda2 and sda3 - in the empty space make a swap partition of 384Mb and then anothere partition format to ext3 and use remainder of the space.

Once that has been done you can exit gparted and start the installation, choose manual when you reach the partition part - pick the linux partition, edit the partition - button near bottom.

In the new edit partition window - pick ext3 (or ext2 journalled) in the Use As boa and / in the mountpoint box, close that window, now continue with the install.

Should be all done...

Reboot when done, windows should be in the menu list when you do, if it's not you can add it if necessary.

---

### Post by michaelbenton1977 on 2008-10-17
In the new edit partition window - pick ext3 (or ext2 journalled) in the Use As boa and / in the mountpoint box, close that window, now continue with the install.



Please clarify the file system.  I see the options [Ext3 journaling file system] and [Ext2 file system] which appears to be the opposite of what you said in the quote.

---

### Post by Elfy on 2008-10-17
Couldn't rememeber how it was - use ext3

---

### Post by michaelbenton1977 on 2008-10-17
Well ForestPixie I thank you for your directions and will look you up in the future for your help was very easy to understand.  I do seem to have a problem with my password now though....

Thank you again and have a great day.


MiCHaEL

---

