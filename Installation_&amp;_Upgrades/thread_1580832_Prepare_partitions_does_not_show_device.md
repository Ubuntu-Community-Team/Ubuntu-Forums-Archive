---
title: "Prepare partitions does not show device"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by guypref on 2010-09-23
Hi,
I try to install 10.04 from CD Rom. At the prepare partitions step, no devices appear.

Some details: 
- I already check the md5sum of the CD.
- GParted see it and I'm able to partition it. But always nothing detected with the prepare step.
- Intel P4 with 80 GB with 1GB of ram
- No windows already installed on the machine.

How can i install it ?

Guy

---

### Post by plucky on 2010-09-24
> **guypref said:**
> Hi,
I try to install 10.04 from CD Rom. At the prepare partitions step, no devices appear.

Some details: 
- I already check the md5sum of the CD.
- GParted see it and I'm able to partition it. But always nothing detected with the prepare step.
- Intel P4 with 80 GB with 1GB of ram
- No windows already installed on the machine.

How can i install it ?

Guy

Did you [MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) the .iso file after you downloaded it?

Did you [Burn the ISO](https://help.ubuntu.com/community/BurningIsoHowto) as slow as possible?

Did you run the CD check in the Live CD menu?

Or you could try [Installation from USB stick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Good Luck

---

### Post by guypref on 2010-09-24
> **plucky said:**
> Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the .iso file after you downloaded it? 

Did you [Burn the ISO]("https://help.ubuntu.com/community/BurningIsoHowto") as slow as possible? 

Did you run the CD check in the Live CD menu? 

Or you could try [Installation from USB stick]("https://help.ubuntu.com/community/Installation/FromUSBStick") 

Good Luck

I did the MD5SUM on the iso file and on the cdrom with dd and they are OK.
I burn it at normal speed but my MD5SUM is ok... I assume that the CD is OK right ?
For the USB stick, if no other hints, I will try it tonight.

More ideas ?

Thank you
Guy

---

### Post by guypref on 2010-09-24
Did you run the CD check in the Live CD menu? 
I did the cd check with dd and MD5SUM in Live CD session on the PC where I want to install it.
Is it what you want to know ?

---

### Post by plucky on 2010-09-24
> **guypref said:**
> Did you run the CD check in the Live CD menu? 
I did the cd check with dd and MD5SUM in Live CD session on the PC where I want to install it.
Is it what you want to know ?

How does that work? Never seen it done like that.

When the Live CD boots,if you press "Enter" when you see the Human = Keyboard symbol,it will take you to a menu where you select your language.

After that it takes you to another menu where it gives you choices to try Ubuntu or install.Another choice is to "check CD for Defects".

That is the test that I want to know runs without errors.

---

### Post by guypref on 2010-09-24
> **plucky said:**
> How does that work? Never seen it done like that.

When the Live CD boots,if you press "Enter" when you see the Human = Keyboard symbol,it will take you to a menu where you select your language.

After that it takes you to another menu where it gives you choices to try Ubuntu or install.Another choice is to "check CD for Defects".

That is the test that I want to know runs without errors.

I did that to check it: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Extract from this page:
===
Now that we know the size of our iso image is  732766208, we can use dd to pipe only 732766208 bytes from our cdrom  device into md5sum. Use a block size of 1 and set count to the size of  the iso image. Note that this will probably take several minutes, so  grab a snack and come back in a while. 
dd if=/dev/cdrom bs=1 count=732766208 | md5sum
732766208+0 records in
732766208+0 records out
24ea1163ea6c9f5dae77de8c49ee7c03  -
732766208 bytes (733 MB) copied, 563.666 s, 1.3 MB/s
===

Of coarse I adjust the size of the iso and the bs=1024 and count=sizeofiso / 1024.

Any way... No error with this and the md5sum match with the one published on the web.
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

I'm not in front of the machine for now so not able to try the Check CD that you propose.

Still ask how to install it ?

Thank's
Guy

---

### Post by srs5694 on 2010-09-24
If I understand correctly, when you go to partition the disk, you're seeing it as completely empty rather than containing whatever partitions you know to be there. If so, please read [my Web page about this problem.](http://www.rodsbooks.com/missing-parts/index.html) If you need more advice, post back with specifics, such as the output of "sudo fdisk -lu" (preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility).

---

### Post by guypref on 2010-09-24
Install Ubuntu does not able to see my HD. 
With or without partition this is what I have:
[IMG]http://picasaweb.google.ca/lh/photo/Sa0WB9bXWBH_Qz4QpLPX5A?feat=directlink[/IMG][IMG]http://picasaweb.google.ca/lh/photo/Sa0WB9bXWBH_Qz4QpLPX5A?feat=directlink[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=170440&stc=1&d=1285377144[/IMG]

 ```
 
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006844e

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$

```Guy

---

### Post by guypref on 2010-09-24
I tried to pass over by patition it manually with GParted but I'm not able to design the root file system.

Now my partitions look like this:

```

ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006844e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   154207934    77103936   83  Linux
/dev/sda2       154207935   156296384     1044225   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```But still no partition showed in the Prepare partitions step (like previous message image).

Is it another way to specify the root file system ?

Guy

---

### Post by srs5694 on 2010-09-24
That's weird. You've clearly got a functional disk, or you wouldn't have been able to use GParted to partition the disk or fdisk to show the partition table to us. I don't see any problems in the partition definitions as revealed by fdisk. You might try typing "dmesg > file.txt" and posting file.txt. (It'll be a big file, so post it as a link.) It's conceivable there'll be a clue buried in there.

---

### Post by guypref on 2010-09-24
There is the dmesg result: [http://www.4shared.com/document/hmMlOXDu/file.html](http://www.4shared.com/document/hmMlOXDu/file.html)

Guy

---

### Post by srs5694 on 2010-09-25
For some reason the kernel is detecting the disk, but it isn't detecting the partitions on the disk. The partitions seem to be valid in fdisk, though. I have some suggestions, but they're shots in the dark:


[list]
[*]Connect the disk to a different SATA port on the motherboard. It's conceivable that there's something flaky about the one you're using.
[*]Go into the BIOS and fiddle with SATA disk settings, such as AHCI mode options.
[*]Use fdisk to repartition the disk. Use the "o" (lowercase letter "O") option to create a fresh partition table, then create new partitions on the disk.
[*]Convert the disk from Master Boot Record (MBR) to GUID Partition Table (GPT) form. You can do this in GParted by selecting Device -> Create Partition table, then clicking the Advanced option and selecting "gpt" from the selection list. When you click Apply, the disk will use GPT. It's best to then create a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) for GRUB 2.
[*]It's possible that there's a subtle hardware fault with the disk. Can you try another one?
[/list]

---

### Post by guypref on 2010-10-04
I tried all of them except changing the disk and it's not work. No other disks to try for now.
 
The server version pass by the same insatallator ?

---

### Post by srs5694 on 2010-10-04
Have you checked the drive's SMART status? If there's a hardware fault, it should show up that way. I'm not sure offhand what SMART utilities, if any, come with the Ubuntu CD that you can run in live CD mode, so I'm not sure offhand how you'd check this. You can probably find some instructions via a Web search.

Aside from more hardware tests, my only suggestion at this point is to try another Linux distribution. You could do a quick test using something like [PartedMagic](http://www.gnu.org/software/parted/) or [System Rescue CD,](http://www.sysresccd.org/) which are emergency systems you could use to see if another kernel/set of utilities can properly access the drive. In a more extreme way, you could try a newer or older Ubuntu or an entirely non-Ubuntu system (Fedora, OpenSUSE, Mandriva, or whatever). My thinking is that there could be some very weird and very specific bug in the kernel, udev, or some other tool that's causing Ubuntu 10.04 to fail to see the partitions on the drive.

---

### Post by guypref on 2010-10-31
I tried the fedora distro and it's tell that the raid metadata was on my hd. I guess it comes from the previous installation. Now, I no more want to have it in raid. 

After installation of mdadm, I tried:

```

ubuntu@ubuntu:~$ sudo mdadm --zero-superblock /dev/sda
mdadm: Unrecognised md component device - /dev/sda

```I tried:

```

ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=1024
1024+0 records in
1024+0 records out
524288 bytes (524 kB) copied, 0.064707 s, 8.1 MB/s

```The ubuntu installer still does not see the drive.

Is this suppose to remove the metadata ?

---

### Post by jrev on 2010-10-31
Here is my hard disk image after the installation of Ubuntu :> jean@jean:~$ fdisk -lu
jean@jean:~$ sudo fdisk -lu

Disque /dev/sda: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x000d6973

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *        2048   613826559   306912256   83  Linux
/dev/sda2       613828606   625141759     5656577    5  Etendue
/dev/sda5       613828608   625141759     5656576   82  Linux swap / Solaris
jean@jean:~$ 


---

### Post by oldfred on 2010-10-31
To remove raid meta data, DO NOT run if you want to keep your RAID:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by ronparent on 2010-10-31
Follow oldfred's advice. What you have is a 'fakeraid' where the disk had been previously used on a MB with a raid chip setup in bios. This has nothing to do with the mdadm software raid. But once used in a fakeraid disk set the data written to the meta data section of your disk will persist until explicitly erased. The dmraid application on the 10.10 live cd has to be used for that. Hopefully this will solve your problem.

---

### Post by guypref on 2010-11-01
> **oldfred said:**
> To remove raid meta data, DO NOT run if you want to keep your RAID:
 
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)
 
This fix my trouble. Ubuntu can now find my HD.
 
Thank's everybody ! I'll enjoy it now !
 
Guy.

---

