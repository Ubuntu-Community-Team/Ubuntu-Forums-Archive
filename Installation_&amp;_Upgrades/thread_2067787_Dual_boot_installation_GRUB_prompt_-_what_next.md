---
title: "Dual boot installation GRUB prompt - what next?"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by Rmgodsie on 2012-10-07
Am new to this.....Please help...have spent three days reading and trying to install ubuntu 11.4 in a dual boot config with xp. wiped whole hard drive installed xp. created partions and installation all went through fine. trying to boot and I get a GNU Grub version 1.99 message followed by a grub prompt.

What happens next? What does one do now? Do I need to do wubi or something? Boot sequence is now hard drive first followed by cd. Have live cd and a windows recovery disk.

i have looked everywhere and am going gogled eyed reading about grub etc. Can anyone help?

i think the installation is on sd5.

---

### Post by darkod on 2012-10-07
Just a reminder, 11.04 is running out of support soon, very soon (if not already out of support).

Don't you want to try something more recent and even better LTS release? (Long Term Supported)

Like the latest 12.04 LTS?

If you still want to try only try and repair the current dual boot, boot the 11.04 cd in live mode and in terminal post the output of:
sudo fdisk -l (small L)
sudo parted -l

---

### Post by Rmgodsie on 2012-10-08
would love to use 12.04 LTS but the problem is the computer does not support PAE? I have an old machine. aspire 2010 :(

---

### Post by Old_Grey_Wolf on 2012-10-08
Try booting using nomodeset option by following these instructions [http://askubuntu.com/questions/147285/unable-to-boot-into-ubuntu-12-04](http://askubuntu.com/questions/147285/unable-to-boot-into-ubuntu-12-04). Those instructions work for older versions as well. 

I think the problem you are having is with the ATI Mobility Radeon graphics card. Support for 11.04 will end 28 October 2012. I would definitely recommend that you try 12.04. 12.04 may actually work with the ATI graphics card.

PAE is not going to help with the Aspire 2010. The Aspire 2010 only supports 2GB of RAM from what I have found searching for the specs. PAE is helpful for computers with 4 GB or more of RAM when using the 32-bit version of Ubuntu. Ubuntu 12.04 should still work on that machine; however, it may be slow due to the single-core 1.5GHz processor. You may find Xubuntu or Lubuntu are faster; however, give Ubuntu a try.

---

### Post by Rmgodsie on 2012-10-09
so i got the 12.04 lts version working....dont know how i did it ..must have been a fluk....see what you mean regarding speed.......ok I have decided to go with lubuntu....can I duel boot this aswell?

---

### Post by Old_Grey_Wolf on 2012-10-09
Yes, you can dual boot Lunbutu.


You don't need to uninstall Ubuntu, just run the install off the CD as usual.

1) When you get to the dialog asking you which partition to install Ubuntu on, choose Manual.
2) Select your Ubuntu partition from the list and set its mount point to '/' (it's on the dropdown menu). Check the format box.
3) Select the swap partition from the list and set it as swap.

---

### Post by Rmgodsie on 2012-10-16
Thanks for all the help. i now have lubuntu installed on machine alongside xp. I have been experimenting over the last week end with Lubuntu. Does ll I need and appears to run much faster on the old laptop than the xp did. However I still get the issue  with the grub prompt? Any ideas?

---

### Post by Rmgodsie on 2012-10-16
lubuntu@lubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91769176

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51202047    25600992+   c  W95 FAT32 (LBA)
/dev/sda2       188112894   312580095    62233601    5  Extended
/dev/sda3        51202048   188112212    68455082+   b  W95 FAT32
/dev/sda5       188112896   311011327    61449216   83  Linux
/dev/sda6       311013376   312580095      783360   82  Linux swap / Solaris

Partition table entries are not in disk order
lubuntu@lubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HM160HC (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  26.2GB  26.2GB  primary   fat32           boot, lba
 3      26.2GB  96.3GB  70.1GB  primary   fat32
 2      96.3GB  160GB   63.7GB  extended
 5      96.3GB  159GB   62.9GB  logical   ext4
 6      159GB   160GB   802MB   logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

lubuntu@lubuntu:~$ ^C
lubuntu@lubuntu:~$ 

This is the info from the disk and the partitions...Any clues here as to why it goes to the grub prompt?

---

### Post by darkod on 2012-10-16
I was under the impression that it's working now. What grub prompt are you talking about exactly? The computer doesn't boot?

If it doesn't, boot the lubuntu cd in live mode, open terminal and try something like this:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot without the cd and see if it helped.

---

### Post by PowerBarry43 on 2012-10-16
You could try downloading a SuperGRUB cd image and boot from that which will allow you to boot into your installed O/S. From there you can run the commands:

```
sudo update-grub
sudo grub-install /dev/sda 
```which should fix your problem.

Barry

---

### Post by Rmgodsie on 2012-10-17
> **darkod said:**
> I was under the impression that it's working now. What grub prompt are you talking about exactly? The computer doesn't boot?

If it doesn't, boot the lubuntu cd in live mode, open terminal and try something like this:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot without the cd and see if it helped.

When I tried this I got a message on the second command saying.
no error reported etc.
when try to then boot into lubuntu I get a short message before the grub prompt saying something about a prefix not being set. then it goes directly to a minimal bash grub message followed by the grub prompt. Can setting up a dual boot system really be this complicated? is the functionality really so sensitive. I realise I am a beginner but the hours i have spent now trying to figure this lot out is into the hundreds. I thought i was ok with computers:):confused: Now I have lost the menu where by I can boot to windows and it goes straight to the minimal bash like editing  message with the GNU Grub version 1.99.

---

### Post by darkod on 2012-10-17
Setting up a dual boot is not complicated, but something is messed up in this case.

Can you boot into live mode and run the bootinfo script from the link in my signature? Post the text from the results.txt file here inside code tags.

Alternatively, you can use boot-repair to create the same results which will give you a link to post.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

They both do the same.

Boot-repair has an automated fix procedure too, in most cases it solves boot problems, so if you want to, you can run it too. You can do all that from live mode.
If you want only to create the bootinfo with boot-repair, select only the option to create the Bootinfo summary, and not the Recommended repair.

---

