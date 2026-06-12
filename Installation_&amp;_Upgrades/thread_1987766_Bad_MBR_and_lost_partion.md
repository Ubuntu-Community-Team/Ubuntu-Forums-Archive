---
title: "Bad MBR and lost partion"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by vinayak11118 on 2012-05-26
Okay.
I had a dual boot system with Win7 and Ubuntu 11.10 but I felt that it had slowed down a lot. So, I decided to install fresh copies of Win7 and 12.04 LTS. So I removed the Ubuntu partitions and formatted Windows and reinstalled it. Windows worked like a charm so I went ahead and created a partition for Ubuntu. Using a live USB I booted into Ubuntu and selected custom partitions....

I selected the 36 GB partition which I had created for installing Ubuntu and continued but it then asked for a swap space (I have heard it doesn't really matter, but I still wanted to create one) so I selected my E drive (which ONLY has work data, movies, games etc) and thought I could chip off 2GB for swap from it. Now here's where I went wrong. I selected the size of the new partition to be 2GB **less **than its actual size and selected **do nothing **in the what do you want to do with the partition option. 

To my horror, it **wiped off** the partition and showed it to bee 100% free !!!

I closed the installation and booted into Windows to see that the E drive wasn't there
and the disk management showed it as an empty partition (100% free).

So I looked up on the internet and downloaded **testdisk **and tried to follow these instructions (although they aren't exactly about my problem) 

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I found that my partition was still there with all the files.  So a put a **L** (logical) infront of the partition and ran **write. **Reboot.

Windows failed to boot...some error about Intel. 

Tried to run bootrec /fixboot but it didn;t recognize any installation of Windows so it didn't work.

Now, all I have is a live USB with 12.04 on it and the internet. I ran fdisk and this is the output :

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf37b1052

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131    6  FAT16
/dev/sda2           81920    66484223    33201152   83  Linux
/dev/sda3        66486272   189364223    61438976    7  HPFS/NTFS/exFAT
/dev/sda4       189364224   976773119   393704448    f  W95 Ext'd (LBA)
/dev/sda5       189366272   976769023   393701376    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 3951 MB, 3951034368 bytes
122 heads, 62 sectors/track, 1020 cylinders, total 7716864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdb2   ?  3272020941   930513678   976730017   16  Hidden FAT16
/dev/sdb3   ?           0           0           0   6f  Unknown
/dev/sdb4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order

Also, I can't install testdisk for some reason :

ubuntu@ubuntu:/$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk

Can someone help ?? I don't care about Windows cause it was fresh and on a separate drive. But I **really, really **need the E drive back. I am on a laptop, if that helps.

---

### Post by darkod on 2012-05-26
I would recommend to stop calling the partition E: once you start dealing with linux tools. It only creates confusion and we have no way of knowing what you refer as E: to.

So, which partition is it that you want to save, the sda2? sda3?

Where is your win7 system partition, and where is the data partition?

---

### Post by vinayak11118 on 2012-05-26
sda4 and sda5 look the same and thats my main data partiton and sda3 is Windows.

One of the sda4/sda5 is the maybe the swap (2000 MB) and the rest is the data partiton.

---

### Post by darkod on 2012-05-26
OK, first of all, don't boot from your hdd, not even windows.

So, from live mode if you try to open sda5, what happens? It looks like the partition was restored correctly by testdisk, it's reported as ntfs partition.

---

### Post by vinayak11118 on 2012-05-26
Okay so I just booted from the live disk and went into the file explorer, and my sda5 (E) is there in the home folder under devices, with ALL the files !:)

So, I'm really nervous about what to do next as I don't want to revert this.

When I open sda3 (windows) it shows all the windows directories.

sda2 (the partition where I wanted to install Ubuntu only has a lost+found folder which I can't open.

---

### Post by darkod on 2012-05-26
I hope you mean you just opened it from the menu on the left, like a partition. Not that it's INSIDE your Home folder. It shouldn't be inside the Home folder, there is no way.

OK, looks like it was restored fine. It won't go away.

Open Gparted and put a boot flag on sda3. Windows can't boot without it, especially if you restored the windows bootloader to the MBR.

After that restart and check if win7 will boot directly. But even if it doesn't, no problem.

---

### Post by darkod on 2012-05-26
Well, you said you never finished the ubuntu install, right? So, forget about it for a moment.

---

### Post by vinayak11118 on 2012-05-26
> **darkod said:**
> I hope you mean you just opened it from the menu on the left, like a partition. Not that it's INSIDE your Home folder. It shouldn't be inside the Home folder, there is no way.
Yup, thats what I meant. Soryy about that.

I put the boot flag and rebooted and Windows opened perfectly and the data partition is now there. Woot! :)

And I'm not sure about trying to install Ubuntu again now. Can't risk all that data and I have no room for backup.

---

### Post by vinayak11118 on 2012-05-26
I can't thank you enough for this !!! My heart was in my mouth for the past hour or so.

I haven't posted here before but I can surely say with great confidence that there is no other operating system which can offer support so quickly and efficiently. :)

---

### Post by darkod on 2012-05-26
Juts install without swap partition and that's it. It seems you were running the 11.10 without swap too.

This has nothing to do with ubuntu. Sorry to say, but you messed up the partition, not the installer. You can't simply try to chop off 2GB from the partition like that during the install.

One option would be to shrink the E: partition for 2GB using win7 Disk Management. When that creates 2GB unallocated space, you can use it during the ubuntu install to create a swap partition from it.

Or simply install without swap.

---

