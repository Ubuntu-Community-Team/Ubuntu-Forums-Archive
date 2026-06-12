---
title: "Trouble building Xubuntu 12.04 USB memory stick boot for USB install"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by mdlueck on 2013-05-23
I am trying to install on a notebook with grumpy CD drive. It is presently loaded with Ubuntu 10.04, and I would like to install Xubuntu 12.04.2 x86 on it.

My desktop machine runs Xubuntu 12.04 x64. I have clean formatted a 4GB SanDisk Cruzer, run through the "Startup Disk Creator", pointing that at the ISO I downloaded: ubuntu-12.04.2-desktop-i386.iso  and selecting the SanDisk USB drive as target. The "Startup Disk Creator" says it completes successfully. Attempting to boot the notebook from the USB stick, however, comes up with an error that it can not read the drive... then sees Grub on the HDD and comes up with the Grub menu.

1) Has the "Startup Disk Creator" been tested with Xubuntu ISO's?
2) Other suggestions?

TIA!

---

### Post by ubfan1 on 2013-05-23
Sometimes startup-disk-creator fails when given an iso for  a system later than the running one.  In those cases (not sure what the 10.04 situation was), try unetbootin to create the usb from the iso.  I have found no differences in running the sticks created via different mechanisms.

---

### Post by mdlueck on 2013-05-24
Thank you for the suggestion to try UNetbootin. I added that package to my Xubuntu 12.04 system, launched it.

The highest versions of Ubuntu it has in its pick list are Ubuntu 11.10. Can not 12.04 create a 12.04 version? :confused:

---

### Post by mdlueck on 2013-05-24
Never mind... I overlooked the option to point UNetbootin at the .ISO file I had downloaded. BRB... ;)

---

### Post by mdlueck on 2013-05-24
I rebuilt the usb stick with UNetbootin and that also shows the error that the notebook does not like what it sees, moves on to Grub.

---

### Post by ubfan1 on 2013-05-24
Did you md5sum check the downloaded iso?  If you did, then maybe you can check the filesystem on the created usb from the running system.  Try a different port for the stick.  Try a different stick.  Do a memory check on the pc if you get the stick to boot.

---

### Post by dentaku65 on 2013-05-25
The only way that I'm able to use usb-creator is to format the usb-key in FAT32 then:
```
sudo usb-creator-gtk --iso=/path/to/iso
```
Then select Erase Disk button (wait a moment that the disk will be available again), choose the desired extra space and finally click on Make Startup Disk button
Done!

---

### Post by sudodus on 2013-05-25
I think there is high probability that the either of usb-creator or unetbootin will make good a USB boot drive. So the problem should be 


a. The iso file is bad (downloading error). Check with ***md5sum***

- The correct md5sums can be found at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- Can another computer boot from this USB drive?


b. The computer does not want to boot from the USB drive.

- Have you set the computer ***boot order*** in the BIOS menu system to boot from USB before the internal HDD?

- Is there a hotkey to press in order to get a menu with devices to boot from?


c. The USB pendrive is bad. All USB pendrives are made for reading and writing files. Most are good for booting, but a few of them are not. Can another computer boot from this USB drive?

---

### Post by mdlueck on 2013-05-26
dentaku65, this was looking promising... however, consistently gets to 38% and crashes.

```
$ sudo usb-creator-gtk --iso=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso
```

Suggestions?

Yes, I have my notebook configured to attempt USB boot before HDD boot. Like I said, it puts up some "disk not ready" type BIOS message, then sails onto Grub from the HDD. So it is attempting.

And yes I md5sum compared the ISO file I downloaded with the checksum file on the webserver... match 100%.

I have formatted the USB drive already, and gotten to 38%, so no point in trying in another system currently.

---

### Post by sudodus on 2013-05-27
> ... however, consistently gets to 38% and crashes.

 ***Please explain!*** At what stage of what process does it get to 38% and crashes?

1. If during the installation, the problem might be ***lack of memory*** (RAM or available space on the HDD) or bad RAM.

Low RAM can be helped with swap, that you make a swap partition before you start installing.

The available space on the HDD can be inspected and fixed before the installation. If already four primary partitions, you need to edit the partition table, at least remove one partition and create an extended partition. If too little free space, you need to remove some files to create enough space.

But before editing partitions, you need to ***back up*** at least your personal data to another drive.


2. If during creation of the boot drive, the USB drive might be bad (bad sectors).

---

### Post by mdlueck on 2013-05-27
> **sudodus said:**
> ***Please explain!*** At what stage of what process does it get to 38% and crashes?

The usb-creator-gtk step, which I provided the command line I used...

> **mdlueck said:**
> dentaku65, this was looking promising... however, consistently gets to 38% and crashes.

```
$ sudo usb-creator-gtk --iso=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso
```

Suggestions?

Perhaps usb-creator-gtk was not tested with Xubuntu? Perhaps x64 Linux does not like building an x86 USB memory stick?

---

### Post by The Cog on 2013-05-27
I've been using dd to create startup USB sticks for some time now - since the usb startup disk creator stopped working a year or so ago. I don't know why they still include it. 

This is the easy way. Plug the stick in and check which device it is (often /dev/sdb or for some reason on my dedktop, /dev/sdf). The command **[FONT=Courier New]sudo blkid[/FONT]** will show what drives are there.
Make sure it's not mounted - unmount it if you need to. Then use this command (change sdb to match your device number):
```
sudo dd if=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso of=/dev/sdb bs=1M
```
and the stick is ready to use.

---

### Post by sudodus on 2013-05-27
In newer versions of Ubuntu ***usb-creator-kde*** is more reliable than it's ***gtk*** cousin, but as *The Cog* wrote ***dd*** is always around and can solve a lot of tricky problems.

It is nick-named 'disk destroyer' because it does what you tell it to do without questions. So double-check and triple-check that you are writing to your USB pendrive, and not to a drive with all your photos ... the margin between miracle and disaster is very narrow, only a single typing error.

---

### Post by The Cog on 2013-05-27
> **sudodus said:**
> It is nick-named 'disk destroyer' because it does what you tell it to do without questions. So double-check and triple-check that you are writing to your USB pendrive, and not to a drive with all your photos ... the margin between miracle and disaster is very narrow, only a single typing error.Amen to that. And I would add, never ever use it after you come back from the pub.

---

### Post by mdlueck on 2013-05-27
> **The Cog said:**
> I've been using dd to create startup USB sticks for some time now - since the usb startup disk creator stopped working a year or so ago. I don't know why they still include it. 
<snip>
Then use this command (change sdb to match your device number):
```
sudo dd if=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso of=/dev/sdb bs=1M
```
and the stick is ready to use.

All right, I tried dd this evening. Two systems, both with BIOS's which support USB boot. Nadda boot! (My desktop machine which is running Xubuntu 12.04 x64, and my notebook which I want to load the x86 version of the same on.)

Perhaps I will try my brand new 32GB stick in stead of my older 4GB stick. Both are SanDisk brand, and I had used the suggested SanDisk Utility to remove the U3 virtual CD from the 4GB stick.

This is very frustrating business!

---

### Post by sudodus on 2013-05-28
1. From where did you download the Xubuntu iso file? And which version is it?

- standard official Xubuntu iso file?
- or some custom build version of Xubuntu?
- 64-bit or 32-bit?

2. Are you sure that the computer is set to boot from a USB drive?

- Sometimes it does not work to set it to boot from USB. Instead, the USB drive is counted as a hard disk drive. So, while the USB drive is inserted, boot into the BIOS menus and change the boot order among the hard disk drives (put the USB drive at the top).

3. I have a couple of old Sandisks with U3. I know that it works to make them bootable with Unetbootin, but I have not tried with dd, where there is U3. If that is the problem, the new 32 GB stick should work for you. My experience is that Sandisk pendrives are easy to make bootable.

4. I have made a special image to make it possible to boot pae kernels in laptops with Pentium M computers using grub2. Such an image can be cloned to USB pendrive and it will boot in most computers with Intel and AMD CPU (at least those made within the last ten years except the newest ones with UEFI). So you can try it and add the Xubuntu iso file or replace Lubuntu with Xubuntu. See this link

[https://help.ubuntu.com/community/grub-n-iso](https://help.ubuntu.com/community/grub-n-iso)

Good luck :-)

---

### Post by mdlueck on 2013-05-28
> **sudodus said:**
> 1. From where did you download the Xubuntu iso file? And which version is it?

- standard official Xubuntu iso file?
- or some custom build version of Xubuntu?
- 64-bit or 32-bit?

I downloaded xubuntu-12.04.2-desktop-i386.iso from the USA mirror. From the filename one can discern...

1) Yes standard official untampered with md5sum matches iso file
2) nay
3) i386 = 32-bit

> **sudodus said:**
> 
2. Are you sure that the computer is set to boot from a USB drive?


I have even gone to the extreme of F12, boot from specific device, the SanDisk USB drive, Enter, blinking cursor forever... (since I switched to building USB drives with dd, prior some error message would come up)

> **sudodus said:**
> 
3. I have a couple of old Sandisks with U3.


And I followed Ubuntu's suggestion to download an official SanDisk U3 removal utility and have removed it.

> **sudodus said:**
> 
 I know that it works to make them bootable with Unetbootin, but I have not tried with dd, **_where there is U3_**. _**If that is the problem**_, the new 32 GB stick should work for you. My experience is that Sandisk pendrives are easy to make bootable.


No more U3, should not be a problem.

I thank you for pointing out pae ISO options... for future use.

---

### Post by mdlueck on 2013-05-28
All right, I tried steps I recalled when making virtual floppy disk for use with VirtualMachines. dd switch bs=512

So... with USB drive unmounted:

```
$ sudo dd if=/dev/null of=/dev/sdb1 bs=512
$ sudo dd if=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso of=/dev/sdb1 bs=512
```

Try to boot... blinking cursor.

```
$ sudo dd if=/dev/null of=/dev/sdb1 bs=1M
$ sudo dd if=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso of=/dev/sdb1 bs=1M
```

Same... try to boot... blinking cursor. hhhmmmmm.....

And I tried the bs=1M set of commands on the SanDisk Cruzer Glide 32GB stick, same blanking cursor attempting to boot.

---

### Post by sudodus on 2013-05-28
Instead of giving up, I meant that you could try 'the pae ISO options' now, as another way to create a USB boot drive. It might work, where your present attempts have failed (Just use the 'grub-n-iso' method *with any Ubuntu family iso file*, that you *copy* onto that usb drive afterwards.

---

### Post by The Cog on 2013-05-28
> **mdlueck said:**
> ```
$ sudo dd if=/dev/null of=/dev/sdb1 bs=1M
$ sudo dd if=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso of=/dev/sdb1 bs=1M
```

This is wrong. You should write the image to sdb, not sdb1. The iso image has its own copy of a partition table etc, it doesn't want to go inside another partition. Use this instead (assuming sdb is the right device):
```
$ sudo dd if=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso of=/dev/sdb bs=1M
```

---

### Post by sudodus on 2013-05-28
> **The Cog said:**
> This is wrong. You should write the image to sdb, not sdb1. The iso image has its own copy of a partition table etc, it doesn't want to go inside another partition. Use this instead (assuming sdb is the right device):
```
$ sudo dd if=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso of=/dev/sdb bs=1M
```

+1

That's right (I overlooked that tiny looking error, which is actually a fundamental error). So there is still hope that dd will work :-)

---

### Post by mdlueck on 2013-05-28
> **The Cog said:**
> This is wrong. You should write the image to sdb, not sdb1. The iso image has its own copy of a partition table etc, it doesn't want to go inside another partition. Use this instead (assuming sdb is the right device):
```
$ sudo dd if=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso of=/dev/sdb bs=1M
```

Great catch. Now at least it comes up with a quick flash of "isolinux.bin bad or missing" sort of error, then right away goes to the HDD Grub screen.

The USB speed was pitiful while writing the ISO to the USB stick, so perhaps a PnP process is hung, time I IPL this machine, so BRB.

---

### Post by mdlueck on 2013-05-28
Most odd indeed! Take a look....

```
mdlueck@jacob:~$ sudo dd if=/dev/null of=/dev/sdb bs=1M
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000620141 s, 0.0 kB/s

mdlueck@jacob:~$ sudo dd if=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso of=/dev/sdb bs=1M
689+1 records in
689+1 records out
722776064 bytes (723 MB) copied, 87.9437 s, 8.2 MB/s

mdlueck@jacob:~$ sudo fdisk /dev/sdb

Command (m for help): p

Disk /dev/sdb: 4047 MB, 4047502848 bytes
19 heads, 24 sectors/track, 17336 cylinders, total 7905279 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x68933a75

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     1411671      705804   **17  Hidden HPFS/NTFS**

Command (m for help):
```

---

### Post by ubfan1 on 2013-05-28
OK, now reverse the dd and copy the usb to a file, and md5sum it again, bet it's corrupted.  I have all sorts of problems with a new Toshiba USB, failed to do a full install to an 8G when on USB 3, failed to install to 8G when on USB2 port, successfully installed to a 4G, then tar failed (many corrupted files, to many to bother trying to fix) copying to 8G, while the same tar copy worked fine on an older HP laptop USB2 to USB2.

---

### Post by mdlueck on 2013-05-28
No surprise that the md5sums do not match in my mind...

```
mdlueck@jacob:~$ sudo dd if=/dev/sdb of=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386-TEST.iso bs=1M
3859+1 records in
3859+1 records out
4047502848 bytes **(4.0 GB)** copied, 191.327 s, 21.2 MB/s

mdlueck@jacob:~$ md5sum ISO/xubuntu-12.04.2-desktop-i386.iso 
5ab48a21e8db6c2136faacf7781ca8d3  ISO/xubuntu-12.04.2-desktop-i386.iso

mdlueck@jacob:~$ md5sum ISO/xubuntu-12.04.2-desktop-i386-TEST.iso 
09157f06514daa1cc25c2e6192f8da03  ISO/xubuntu-12.04.2-desktop-i386-TEST.iso

```

The TEST.iso file is of the entire 4GB stick. I think I shall try my new 32GB stick.

---

### Post by mdlueck on 2013-05-28
> **mdlueck said:**
> I think I shall try my new 32GB stick.

And same error as in #22 on this thread using that 32GB stick. Good night all...

---

### Post by sudodus on 2013-05-28
> **mdlueck said:**
> Most odd indeed! Take a look....

```
mdlueck@jacob:~$ sudo dd if=/dev/null of=/dev/sdb bs=1M
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000620141 s, 0.0 kB/s

```

The command above is wrong and also not necessary. /dev/null is for output to nothing (switching off the output), while /dev/zero is for input of zeros.
> 
```

mdlueck@jacob:~$ sudo dd if=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386.iso of=/dev/sdb bs=1M
689+1 records in
689+1 records out
722776064 bytes (723 MB) copied, 87.9437 s, 8.2 MB/s

```

This looks good. I think the iso file was cloned successfully.
> 
```

mdlueck@jacob:~$ sudo fdisk /dev/sdb

Command (m for help): p

Disk /dev/sdb: 4047 MB, 4047502848 bytes
19 heads, 24 sectors/track, 17336 cylinders, total 7905279 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x68933a75

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     1411671      705804   **17  Hidden HPFS/NTFS**

Command (m for help):
```

I think a normal PC computer with Intel or AMD CPU should boot from this USB drive, unless it has UEFI. A power PC won't boot. If it is a normal PC computer and won't boot, I suggest that you try the USB drive in another PC (maybe a PC of a friend of colleague).

We need to find out if the USB drive is a good for booting. Now we don't know what is causing your problem.

- The USB drive might be bad somehow

- The computer might have problems to boot from USB

- Have you checked if the RAM is good?

---

### Post by sudodus on 2013-05-29
> **mdlueck said:**
> No surprise that the md5sums do not match in my mind...

```
mdlueck@jacob:~$ sudo dd if=/dev/sdb of=/home/mdlueck/ISO/xubuntu-12.04.2-desktop-i386-TEST.iso bs=1M
3859+1 records in
3859+1 records out
4047502848 bytes **(4.0 GB)** copied, 191.327 s, 21.2 MB/s

mdlueck@jacob:~$ md5sum ISO/xubuntu-12.04.2-desktop-i386.iso 
5ab48a21e8db6c2136faacf7781ca8d3  ISO/xubuntu-12.04.2-desktop-i386.iso

mdlueck@jacob:~$ md5sum ISO/xubuntu-12.04.2-desktop-i386-TEST.iso 
09157f06514daa1cc25c2e6192f8da03  ISO/xubuntu-12.04.2-desktop-i386-TEST.iso

```

The TEST.iso file is of the entire 4GB stick. I think I shall try my new 32GB stick.

This test did not work, because you cloned the whole drive to the TEST.iso file. You need to write exactly as many bytes from the pendrive to the TEST.iso file, as you wrote from the original iso file to the pendrive.

---

### Post by dentaku65 on 2013-05-29
> **mdlueck said:**
> dentaku65, this was looking promising... however, consistently gets to 38% and crashes.
...

Did you formatted twice the usb key?
Or, even better, did you try with a different usb key?

---

### Post by mdlueck on 2013-05-29
> **sudodus said:**
> The command above is wrong and also not necessary. /dev/null is for output to nothing (switching off the output), while /dev/zero is for input of zeros.

Thank you for the reminder of that. Noted.
> **sudodus said:**
> I think a normal PC computer with Intel or AMD CPU should boot from this USB drive, unless it has UEFI.

Linux writing a partition flagging it:
```
Id  System
17  Hidden HPFS/NTFS
```
rrrrr?????

And I suppose I should be able to mount the ISO I downloaded and fdisk the ISO to compare partition tables, no?
> **sudodus said:**
> - The USB drive might be bad somehow
I am dealing with two SanDisk brand drives.
> **sudodus said:**
> - The computer might have problems to boot from USB
Two computers, both with USB boot in the BIOS, though this is the first I have tried such.
> **sudodus said:**
> - Have you checked if the RAM is good?
Yes, all systems always with MemTest on the Ubuntu CD! ;)

---

### Post by mdlueck on 2013-05-29
> **sudodus said:**
> This test did not work, because you cloned the whole drive to the TEST.iso file. You need to write exactly as many bytes from the pendrive to the TEST.iso file, as you wrote from the original iso file to the pendrive.

Please suggest syntax to capture with dd only a set byte count. Thanks.

---

### Post by mdlueck on 2013-05-29
> **dentaku65 said:**
> Did you formatted twice the usb key?

As you can see from the thread, I have moved on from tinkering with the GUI create a USB Linux boot and am attempting to successfully produce one via dd command line syntax.

Each time the GUI tool would crash, I would clean reformat the USB stick to start over... though only once. Do you really think that formatting it twice before using the GUI tool would have been the critical step?

> **dentaku65 said:**
> Or, even better, did you try with a different usb key?

I am attempting with the GUI on the 32GB stick presently... And the verdict on that idea is that it completes successfully, and placing it in the notebook, F12, select boot device, SanDisk USB, BIOS reports "Missing Operating System". waaa waaa waaa... :(

---

### Post by sudodus on 2013-05-30
You have really tried and checked a lot of things. I'm starting to think your Xubuntu iso file is not suitable for your combination of USB pendrives and computers. So I will suggest that you try

1. some other flavour and version of Ubuntu, for example Lubuntu 12.04, 12.10 or 13.04 (and use dd to clone it to the pendrive).
 
2. some other method to boot, for example the 'grub and iso method', that works very well for me with Ubuntu desktop iso files (but not every other iso file). Use my prepared image according to

[http://http://https://help.ubuntu.com/community/grub-n-iso](http://http://https://help.ubuntu.com/community/grub-n-iso)

or build the system yourself according to

[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

Good luck :-)

---

### Post by dentaku65 on 2013-05-30
> **mdlueck said:**
> 
Each time the GUI tool would crash, I would clean reformat the USB stick to start over... though only once. Do you really think that formatting it twice before using the GUI tool would have been the critical step?
... :(

I can speak only for my experience with a very old laptop; I was able to create a bootable USB with usb-disk-creator only as I indicated, but the indication was: format the drive before, then inside the gui format again, not twice before... anyway, out of curiosity, did you try another tool for example Unetbootin or Imagewriter?

---

### Post by sudodus on 2013-05-30
> **mdlueck said:**
> Please suggest syntax to capture with dd only a set byte count. Thanks.

See ```
man dd
``` Use the operand ***count***
```

       count=BLOCKS
              copy only BLOCKS input blocks

```
If the number of bytes is not a multiple of 512, you need to adjust the block-size with the ***bs*** operand

```
$ bc -l
bc 1.06.95
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 
722776064/512
1411672.00000000000000000000
```

It is a multiple, so you can use the default blocksize (or specify it if you like)

```
bs=512 count=1411672
```

---

### Post by mdlueck on 2013-06-03
> **dentaku65 said:**
> I can speak only for my experience with a very old laptop; I was able to create a bootable USB with usb-disk-creator only as I indicated, but the indication was: format the drive before, then inside the gui format again, not twice before... anyway, out of curiosity, did you try another tool for example Unetbootin or Imagewriter?

Well dentaku65, blanking the USB stick with /dev/zero instead of /dev/null seems to have been the trick to get usb-disk-creator not to crash at 38% on the 4GB SanDisk.

Still refuses to boot in the notebook.

Suggestions how else to load Xubuntu 12.04.2 on this notebook, which has a working boot of Ubuntu 10.04?

I put in the burned CD to the notebook drive, it thinks I have just inserted a blank CD - offering to bring up CD burner software. If I put it in my desktop (running Xubuntu 12.04 x64) it reads the CD and offers to launch the package manager. (Which is what I would expect.)

So I have been trying to get USB stick install to work. Which fails.

Any other suggestions? TIA!

---

### Post by sudodus on 2013-06-04
Did you try according to posts #33 and #35?

---

### Post by dentaku65 on 2013-06-04
> **mdlueck said:**
> 
Suggestions how else to load Xubuntu 12.04.2 on this notebook, which has a working boot of Ubuntu 10.04?

You meant that you have a working Ubuntu on that machine?
If so, you can install Xubuntu along side with Ubuntu:
```
sudo apt-get install xubuntu-desktop
```
Or you can choose to replace Ubuntu via Psychocats 'pure Xfce' instructions:
[http://www.psychocats.net/ubuntu/purexubuntuprecise](http://www.psychocats.net/ubuntu/purexubuntuprecise)
I personally did the Psychocats but for 10.04 in order to skip Unity on do-release upgrade

---

### Post by mdlueck on 2013-06-04
> **dentaku65 said:**
> You meant that you have a working Ubuntu on that machine?
If so, you can install Xubuntu along side with Ubuntu:
```
sudo apt-get install xubuntu-desktop
```
Or you can choose to replace Ubuntu via Psychocats 'pure Xfce' instructions:
[http://www.psychocats.net/ubuntu/purexubuntuprecise](http://www.psychocats.net/ubuntu/purexubuntuprecise)
I personally did the Psychocats but for 10.04 in order to skip Unity on do-release upgrade

Oh, so do the lateral switch over to Xubuntu on 10.04, then perform the LTS upgrade from 10.04 to 12.04? I had not thought of that.

Yes, I have a beautifully working 10.04, which is no longer getting updates, so I desire to move to 12.04. That is all.

So there was an Xubuntu 10.04... hhhmmm... neat slight of hands, thanks dentaku65! ;)

(Apparently so... [http://en.wikipedia.org/wiki/Xubuntu](http://en.wikipedia.org/wiki/Xubuntu)  My my Xubuntu has been around for QUITE a while...)

---

### Post by mdlueck on 2013-06-04
> **sudodus said:**
> Did you try according to posts #33 and #35?

I forgot to test this once I realized I was not really blanking the USB stick by writing /dev/null to it. Seeing blanking with /dev/zero have the originally tried usb-disk-creator actually complete successfully on the 4GB SanDisk, I forgot your suggestions in #33 / #35.

I am wiping the 32GB SanDisk presently, and will double check if the different stick makes the difference. If even still that does not work, perhaps I will morph my working installation of Ubuntu to Xubuntu and upgrade, etc...

---

### Post by sudodus on 2013-06-04
Yes, you can install ***xubuntu-desktop*** *dentaku65* or 'only' ***xfce4*** into Ubuntu 10.04 and upgrade to 12.04. You can also upgrade to 12.04 and install xubuntu-desktop ...

I think the upgrade process has higher probability to succeed if you have less packages installed, so I would upgrade first and install xubuntu-desktop later, or install xubuntu-desktop and clean out the Ubuntu desktop before upgrading, using the link to psychocats, that *dentaku65* provided in post #38.

But I think you should really try Xubuntu and Lubuntu live before upgrading, because in general, the success rate is much higher with live sessions and fresh installs compared to upgrading between versions. If you have no luck with Xubuntu or Lubuntu, chances are that you will have problems after upgrading from 10.04.

-o-

I upgraded my production system from Ubuntu 10.04 to Ubuntu 12.04.1 (now 12.04.2), but I had some issues before I was happy with it. I installed xubuntu-desktop and lubuntu-desktop into 12.04. I am running it as ***Lubuntu most of the time*** because it is fast and smooth in my ageing hp workstation xw8400 with two double core Xeon CPUs.

---

### Post by dentaku65 on 2013-06-04
My experience was to use the documentation of Psychocats in order to convert my 2 production machines from Ubuntu (Gnome) to Xubuntu (Xfce) on 10.04, then I did a do-release upgrade to 12.04. Both machines worked perfectly.

---

### Post by mdlueck on 2013-06-05
Clearing off the 32GB stick with /dev/zero takes 2.2Hr, building via usb-disk-creator and results in a "can not boot" BIOS message. Enough already!

Well after a long battle, the notebook is successfully running Xubuntu 12.04!!! :D

My technique was to do the lateral move from ubuntu-deskop to xubuntu-desktop while on 10.04, remove ubuntu-desktop, then go through the LTS upgrade to 12.04. Whole day pretty much, but SUCCESS none the less.

Thank you to all for your much appreciated assistance.

---

### Post by sudodus on 2013-06-06
Congratulations :KS

Your case was unusual, it worked better to upgrade than to test the new system live. You really had to fight for it.

---

