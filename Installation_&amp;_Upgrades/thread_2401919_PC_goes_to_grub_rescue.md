---
title: "PC goes to grub rescue"
date: 2018-09-24
forum: Installation &amp; Upgrades
---

### Post by jv69 on 2018-09-24
Hello, 
After running the "dd" command thinking i was creating a bootable CD, i wipe sda or sda1 or unmounted it.:confused: My PC only comes up in grub rescue mode.

This is the output from "ls"
grub rescue > ls 
(hd0) , (hd01,msdos5), (hd0, msdos1), (fd0)

For each list, i performed the following:
1) set root=(hd0)
2) set prefix=(hd0)/boot/grub
3) insmod normal
Output:  "unknown filesystem"
4) normal

Then i made a Live Xubuntu USB and downloaded Boot-repair. Not sure if it detected the PC's harddrive. 

Here is the output from Boot-repair
[http://paste.ubuntu.com/p/B6CVKCRZX8/](http://paste.ubuntu.com/p/B6CVKCRZX8/)

Luckily i did a backup. Does anyone have time to look at the output? 
thank you

---

### Post by oldfred on 2018-09-24
Your sda shows a very large Linux partition, but internally it says ISO9660.
The ISO is only about 2GB, but the first 2GB is vital for system.

But surprised it shows partition table. You may have (incorrectly) written to sda1? But that saved partition table in sda.
 Normally the dd process just creates a ISO hybrid DVD/flash drive image that then normal partition tools cannot even read as random data. You have to zero out first sector of drive can create new MBR, for partition tools to have space to write updates.

Linux writes data somewhat randomly into the entire partition. Since 200GB drive and only 2GB overwritten and swap not large, you probably still have most of your data somewhere on drive. 
I might see what testdisk shows. And if deeper search show files backup/copy them immediately.
If not and you need to recover data then you can use photorec which is part of testdisk.

       Testdisk Instructions, new versions use sectors, old ones were CHS
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
Photorec requires another drive with enough room for all data your recover. And it does not recover full file names. It took me weeks to compare backup to all the files it recovered as it also recovered every deleted file, and a few partial files that looked like a full file to photorec.
       
 [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 
    

You may recover a mountable file system, but not any data from first 2GB, so not a working system by using fsck and a backup superblock that is beyond the first 2GB of drive.

       [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro 


This is one reason I prefer gpt as partition table is stored at both beginning & end of drive. In your case it may not have saved much since you still seem to have MBR partition table.

---

### Post by jv69 on 2018-09-27
It looks like i have a corrupted partition.  (still learning how too)



[IMG]/home/joev/Desktop/Screenshot_2018-09-27_10-07-07.png[/IMG]

---

### Post by jv69 on 2018-09-27
[ATTACH=CONFIG]281195[/ATTACH]

The image of damaged partition.

---

### Post by oldfred on 2018-09-27
Since you have partition table, testdisk shows the partitions. Can you do deeper search?

Did you try e2fsck?

---

### Post by jv69 on 2018-09-27
Testdisk is reporting that the partitions are not recoverable.
[ATTACH=CONFIG]281198[/ATTACH][ATTACH=CONFIG]281198[/ATTACH]

---

### Post by jv69 on 2018-09-27
Looking how to find a super block size value
[ATTACH=CONFIG]281201[/ATTACH]

---

### Post by yancek on 2018-09-27
Have you tried running fsck on the partition (sda1) rather than the device (sda)?

---

### Post by jv69 on 2018-09-27
Yes, it returned 
-> sudo fsck /dev/sda1
 fsck from util-linux 2.31.1

Then i ran: sudo  e2fsck -b 8193 -y /dev/sda1
Not sure if that number is correct.  I think this is due when i tried to make a bootable USB with the DBAN iso ( to wipe another computer for linux install) 

e2fsck 1.44.1 (24-Mar-2018)
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

/dev/sda1 contains a iso9660 file system labelled 'DBAN

---

### Post by jv69 on 2018-09-28
Now my harddrive is mounted to the live USB drive. Not sure how

---

