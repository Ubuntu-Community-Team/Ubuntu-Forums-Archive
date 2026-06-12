---
title: "[SOLVED] grub-install fails"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by mgw854 on 2008-02-23
I just built a new computer last week, and I installed Windows on it (I know, I know).  This weekend, I was going to install Ubuntu.  I tried using an AMD64 7.10 disk, and GRUB failed to install.  I then tried using an AMD64 8.04 alpha 5 disk, but again, GRUB failed to install.  I am running with two SATA drives, a DVD and an HDD.  The HDD is labeled as "sda".  There are three partitions on it: sda1 for Windows, sda2 for my files, and sda3 for Ubuntu.  I have browsed other forum topics, but I can't find anything that specifically relates to this specific set-up.  If anyone has any suggestions, I would be more than willing to try them.

---

### Post by Pumalite on 2008-02-23
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by mgw854 on 2008-02-23
None of those specifically address my problem- I know how to partition a drive,  and I know how to install Ubuntu.  My issue is specifically related to a fatal grub-install error, which none of these articles mention.

---

### Post by Pumalite on 2008-02-23
Post the exact error message.

---

### Post by mgw854 on 2008-02-23
Here is the message:
> 
Executing 'grub-install (hd0)' failed.
This is a fatal error.


---

### Post by Pumalite on 2008-02-23
Do you have a Raid Array?
Post:
sudo fdisk -lu

---

### Post by mgw854 on 2008-02-23
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcabcb595

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   314574847   157286400    7  HPFS/NTFS
/dev/sda2       314574848   576718847   131072000    7  HPFS/NTFS
/dev/sda3       576718848   625137663    24209408    6  FAT16

This is the return of fdisk -lu.  One thing though- the sda3 disk returns itself as a FAT16 disk, but it is formatted as ext3.

---

### Post by dstew on 2008-02-23
I have seen the grub fatal error in certain hardware situations. It seems to be a bug in the installer. The workaround is to format the linux partiton as ext2 instead of ext3. Then grub will install. Then, the ext2 file system can be converted to an ext3 after the installation is complete. See [this thread]("http://ubuntuforums.org/showthread.php?t=193103").

And, the fact that fdisk shows the partition as FAT16 indicates you will probably need to reformat anyway. So try ext2, and then use tunefs to change to ext3 after grub is installed.

---

### Post by Pumalite on 2008-02-23
How much space did you allocate for Ubuntu in sda3?

---

### Post by mgw854 on 2008-02-23
Ubuntu has a good 20 some gigs of space to install on.  I'll try formatting the drive in ext2 and see if that does anything.

---

### Post by Pumalite on 2008-02-23
Dont do that. Install Ubuntu, go manual and create 2 partitions in sda3:
About 18 GB for '/'' (mount point '/')
The rest for /swap (mount point swap)
Then hit continue.
Make sure in step 8 to check (Advanced Tab) and make sure it says: (hd0)

---

### Post by mgw854 on 2008-02-23
Well, I tried installing Ubuntu in ext2 anyways, and it works like a dream.  I have no need for a swap partition, I have four gigs of ram installed on the computer.  I'm doing some customization, and then I'll upgrade to ext3.  Thanks for the help!

---

