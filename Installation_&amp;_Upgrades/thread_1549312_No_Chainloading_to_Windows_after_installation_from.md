---
title: "No Chainloading to Windows after installation from stratch"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by tayran on 2010-08-09
Hi all,

I recently installed Kubuntu 10.04 to my machine. Beforehand I had installed windows XP thinking that kubuntu will detect it and adjust grub according to that.

After installing kubuntu to my surprise there were no other operating systems visible in the grub boot menu.

So I tried reinstalling grub with sudo update-grub command and here is the result:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done

..and this is the result of sudo fdisk -l command:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13131312

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2554    20506624   83  Linux
/dev/sda2            2554       19456   135771649    f  W95 Ext'd (LBA)
/dev/sda5           16191       19456    26234113+   7  HPFS/NTFS
/dev/sda6            2554       15878   107030528   83  Linux
/dev/sda7           15879       16190     2505728   82  Linux swap / Solaris

Windows is installed on partition sda5. You can also find as an attachment how gparted sees the partitions.

---

### Post by oldfred on 2010-08-10
Did you have another copy of windows in sda1? Windows in a logical partition will only boot thru the primary active (boot flag) partition with the first windows install. See link for details.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by tayran on 2010-08-11
Thanks for the reply. I took a look of the link you gave but I saw it was solely about windows boot loaders. Also to mention that I you can see in the picture I have attached that my sda1 partition is formatted as ext4 and it is the root partition of kubuntu installation. Then comes an extended partition and the first partition in this extended partition is used as home folder for kubuntu installation.

After the linux partitions comes the partition where windows xp is installed. I suspect that the windows partition may have been the first one and the primary partition in order to boot because that was the case in my previous installations.

I don't want to go into a costly partition moving adventure unless being sure it will work.

---

### Post by Sef on 2010-08-11
oldfred is correct.  Your Windows partition is on an extended partition, so it will not work.  You will need to move it to or install it on sda1 to have it boot up.

---

### Post by tayran on 2010-08-11
Now I need some way to take a backup of the current partitions, rearrange them and restore backup data to related partitions.

I know that I can use some programs like norton ghost to take an image of windows partitions but the tools I am using does not recognize ext4 file system and I need a way to safely do the same thing for the linux ext4 partitions. I don't want to take a byte to byte copy with dd command because the data is sparse and I am not sure simply archiving everything with tar command and then installing grub with a live cd will work.

Can you recommend any live cds to handle that ?

Thanks

---

### Post by oldfred on 2010-08-11
I have not used any of these as I backup /home, a list of installed applications and some special configs in /etc.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

What can speed up the operation is using ntfsclone rather than dd. This program backs up only the used sectors on an NTFS partition. It's installed as part of the ntfsprogs package. Type "man ntfsclone" for details. There are some examples at the end of the man page, such as:
ntfsclone --save-image --output backup.img /dev/hda1

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
[http://clonezilla.org/](http://clonezilla.org/)

If you want to experiment after backing up you can redefine your sda5 partition to be sda2. 'All' you have to do is edit the partition table to make the extended smaller and renumber sda5 to sda2. This could work in your case since you have a spare primary and your windows is the last one on the drive. I have not done it but these very experienced users have.

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

Use sfdisk to edit partitions
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

---

