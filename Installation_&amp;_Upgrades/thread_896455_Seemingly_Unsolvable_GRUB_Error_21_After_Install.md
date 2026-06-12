---
title: "Seemingly Unsolvable: GRUB Error 21 After Install"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by kmolnar on 2008-08-21
Okay, I have spent several weeks attempting to get this working, researching various fixes for GRUB Error 21, and in the end have come up utterly empty-handed, so I really hope someone has an idea of what I am missing here.

I am trying to get Ubuntu 8.04 installed on my desktop.

I have a single SATA drive ("sda"), partitioned as follows:

---
sda0 ntfs (Windows XP Pro)
sda4 ext2 (root for Ubuntu)
sda5 linux-swap (swap for Ubuntu)
---

Here are solutions I have seen which did not work (just to get them out of the way):

1. Change BIOS settings for the drive to LBA - These settings are not available, as it is not an IDE drive.

2. Move the Ubuntu boot partition to within 137 GB of the start of the drive - Tried this, didn't work.

3. Check menu.lst settings - summarized, it's trying to boot Ubuntu at (hd0,3) which is, as I understand, correct for sda4. I will post the relevant portions of my menu.lst later, though.

4. Change jumpers / slave/master / etc. - Again, SATA drive. No jumpers, no slave/master settings, just a SATA cable plugged into SATA0 (as per the label on the motherboard).

5. Reinstall GRUB - I must have done this 100 times by now - the good part is that now I have it memorized. Hah! root (hd0,4) setup (hd0) ... could do that all day (to no effect, appparently).

6. Use the magical awesome Super Grub Disk - SGD has a whole bunch of options and features, and none of them seems to work for my issue. I just get lots and lots of "Error 15 - file not found" messages, and even encounter a problem trying to restore the Windows bootloader with it.

So far the only thing that has actually worked has been using the Windows XP install disk's recovery console to get XP booting again (via "fixmbr").

I would really, really, *really* like to get Hardy working on my desktop, 'cause I've been running it painlessly on my laptop since launch (and before that, Gutsy (and before that, Feisty!)), so I'm not really sure why my desktop has such a massive problem with it.

So yeah, if anyone can help, they can automatically consider themselves extremely, nay, palpably awesome in advance! =)

*crosses fingers*

Oh, and I should probably mention that I have access to the Linux installation from a LiveCD (so I know it is there) and can see the partitions just fine from XP as well, so near as I can tell both the install itself and the partition tables are uncorrupted.

[B]SOLUTION:
Apparently, there are two issues on which GRUB, the Linux kernel, and my MSI P965 Neo motherboard disagree:

Problem the first: GRUB Error 21.
Fix: Move SATA drive out of port 1, because GRUB and JMicron don't play well.

Problem the second: BusyBox
Fix: press 'e' to edit the Ubuntu boot option, then 'e' again on the kernel line, replace "quiet splash" with "all_generic_ide", press enter to accept, press 'b' to boot.

(Long-term fix for the latter: make the change in /boot/grub/menu.lst)

Thanks to everyone who helped me figure this out!
[/B]

---

### Post by Dark-archon on 2008-08-21
you could try wubi and avoid grub all together (it uses the windows bootloader)

---

### Post by caljohnsmith on 2008-08-21
Hi kmolnar, how about booting a Live CD and posting the output of all the following:
```
sudo fdisk -lu
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
sudo mount /dev/sda4 /mnt
ls -l /mnt/boot/grub
cat /mnt/boot/grub/device.map
sudo grub
grub> geometry (hd0)
grub> find /boot/grub/stage1
grub> quit
```
Those commands will at least give us useful info about your setup and hopefully help to narrow down your problem.

---

### Post by redester on 2008-08-21
****

Be sure to check /boot/grub/menu.lst to makee sure the drive/partitions are to the proper one.  My installation pointed to hd1 instead of hd0.  Editing fixed it.
Why it did that is anyones guess.  I see several having a problem related to this!

Ray

---

### Post by kmolnar on 2008-08-21
> **caljohnsmith said:**
> Hi kmolnar, how about booting a Live CD and posting the output of all the following:
```
sudo fdisk -lu
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
sudo mount /dev/sda4 /mnt
ls -l /mnt/boot/grub
cat /mnt/boot/grub/device.map
sudo grub
grub> geometry (hd0)
grub> find /boot/grub/stage1
grub> quit
```
Those commands will at least give us useful info about your setup and hopefully help to narrow down your problem.

The output:
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    86879519    43439728+   7  HPFS/NTFS
/dev/sda2        86879520   625137344   269128912+   5  Extended
/dev/sda5        86879583   612992204   263056311   83  Linux
/dev/sda6       612992268   625137344     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1015db5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     4030463     2015216    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 ff04                                   
2 bytes (2 B) copied0000002
, 3.3479e-05 s, 59.7 kB/s
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ ls -l /mnt/boot/grub
total 196
-rw-r--r-- 1 root ubuntu    197 2008-08-20 12:12 default
-rw-r--r-- 1 root ubuntu     15 2008-08-20 12:12 device.map
-rw-r--r-- 1 root ubuntu   8056 2008-08-20 12:12 e2fs_stage1_5
-rw-r--r-- 1 root ubuntu   7904 2008-08-20 12:12 fat_stage1_5
-rw-r--r-- 1 root ubuntu     16 2008-08-20 12:12 installed-version
-rw-r--r-- 1 root ubuntu   8608 2008-08-20 12:12 jfs_stage1_5
-rw-r--r-- 1 root root     4576 2008-08-20 12:12 menu.lst
-rw-r--r-- 1 root ubuntu   7324 2008-08-20 12:12 minix_stage1_5
-rw-r--r-- 1 root ubuntu   9632 2008-08-20 12:12 reiserfs_stage1_5
-rw-r--r-- 1 root ubuntu    512 2008-08-20 12:12 stage1
-rw-r--r-- 1 root ubuntu 108356 2008-08-20 12:12 stage2
-rw-r--r-- 1 root ubuntu   9276 2008-08-20 12:12 xfs_stage1_5
ubuntu@ubuntu:~$ cat /mnt/boot/grub/device.map
(hd0)	/dev/sda
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x82

grub> find /boot/grub/stage1
 (hd0,4)
 (hd1,0)

grub> quit


```

I was remembering the partition numbers wrong - I had shifted them into 0-basis (I was tired after an O-O data structures class, heh). So it's sda5 and sda6, not sda4 and sda5

menu.lst has (hd0,4) listed for the Ubuntu boot. I believe the (hd1,0) returned by grub find refers to my bootable USB flash drive (/dev/sdb) (Super Grub Disk USB is installed on it), and obviously the second result from fdisk -lu refers to the same.

Here are the relevant portions of menu.lst:

```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1d75621b-5e0a-49b7-aa0e-c0e6cde77fe5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1d75621b-5e0a-49b7-aa0e-c0e6cde77fe5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Possibly of note: when viewed in gparted, sda5 and sda6 are indented beneath sda2.

This hasn't shed any light for me, but maybe there's something I'm not seeing here.

I should note that at the moment, the NT bootloader is installed, not GRUB. I will reinstall GRUB to the MBR and post an update if any of these results differ.

Thanks for your help thus far. =)

---

### Post by kmolnar on 2008-08-21
> **Dark-archon said:**
> you could try wubi and avoid grub all together (it uses the windows bootloader)

I did try this. It did work. It did not, however, for some reason, install my wifi card, which even the LiveCD does, and after fighting with bc43xx-fwcutter and the like for an hour or two, I gave up and decided I might as well fight with grub as well. =)

---

### Post by kmolnar on 2008-08-21
Update: after reinstalling grub to the MBR, all results remain identical as above.

```

grub> root (hd0,4)
grub> setup (hd0)
grub> quit

```

---

### Post by caljohnsmith on 2008-08-21
Everything you posted looks in perfect order. It seems like it must have something to do with your BIOS. I know you said you don't have LBA mode, but are there any other HDD settings you can change in BIOS? Can you upgrade your BIOS maybe? And just to confirm, was Windows working fine until you installed Hardy + Grub?

---

### Post by DavidTangye on 2008-08-21
My only guess is that perhaps > 2. Move the Ubuntu boot partition to within 137 GB of the start of the drive - Tried this, didn't workdid something odd like not start the partition on a cylinder boundary or something like that. I am a bit hazy on the exact issues regarding this, as I avoid fancy partition manglers and do not move stuff around for this very reason: I have seen too many people come to grief in the past, so I just dont go there while I do not need to.

---

### Post by caljohnsmith on 2008-08-22
Kmolnar, one thing I didn't notice before: what is on your sdb HDD? fdisk says it's a FAT partition, but what surprised me is that Grub said it found a /boot/grub/stage1 file on that HDD. Do you even have a /boot/grub directory on that HDD? 

Please also post the output of:
```
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sdb bs=512 count=3 | hexdump -C
```

---

### Post by kmolnar on 2008-08-22
> **caljohnsmith said:**
> Kmolnar, one thing I didn't notice before: what is on your sdb HDD? fdisk says it's a FAT partition, but what surprised me is that Grub said it found a /boot/grub/stage1 file on that HDD. Do you even have a /boot/grub directory on that HDD? 

Please also post the output of:
```
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sdb bs=512 count=3 | hexdump -C
```

Yes, there is a /boot/grub directory on it, but it's not a hard disk; it's a bootable flash drive. It has Super Grub Disk USB installed on it. Its boot stuff is unrelated to this issue and is in working order. I was just using it to transfer the logs from the diagnostic steps I performed over to my laptop, so I could reply with them.

> **DavidTangye said:**
> My only guess is that perhaps did something odd like not start the partition on a cylinder boundary or something like that. I am a bit hazy on the exact issues regarding this, as I avoid fancy partition manglers and do not move stuff around for this very reason: I have seen too many people come to grief in the past, so I just dont go there while I do not need to.

Regarding my having tried moving the boot partition, I meant I had tried blanking the drive and formatting it with Ubuntu first, which would achieve the same effect, and it did not work. I haven't tried shuffling partitions around or anything crazy like that. =)

After that failed, I reinstalled Windows to cover the disk, then most recently used Ubuntu's default "resize the Windows partition" install method to arrive at my current configuration.

> **caljohnsmith said:**
> Everything you posted looks in perfect order. It seems like it must have something to do with your BIOS. I know you said you don't have LBA mode, but are there any other HDD settings you can change in BIOS? Can you upgrade your BIOS maybe? And just to confirm, was Windows working fine until you installed Hardy + Grub?

Regarding BIOS settings - the only such settings in the BIOS pertain to IDE drives, not SATA drives (these being under the "Standard CMOS Settings" menu, which lists no drives at all. My Western Digital 300GB drive (sda) shows up, instead, only on the boot order screen, which has no such options. I have combed through every screen in the BIOS settings and can't find anything related to this issue.

Regarding Windows - yes, it was working fine until GRUB got installed in the MBR. Using the Windows recovery console's fixmbr command restores the NT bootloader to normal working order, and all the partition changes are still reflected in and respected by Windows' disk management tools.

Regarding flashing the BIOS... I am wary of doing so, but I have been thinking for some time now that it might be unavoidable. I'll see if there have been any BIOS updates for my motherboard. Worst case scenario is, I suppose, reflashing with the old BIOS (the mobo has a handy built-in restore feature via setting a jumper) or possibly getting a new mobo, and I'm kind of due for an upgrade there anyway.

---

### Post by kmolnar on 2008-08-22
Update: I have checked online and my bios (AwardBIOS) is the latest version available.

Motherboard: Micro-Star Int'l MSI-7235 P965 Neo
MSI Website: [http://global.msi.com.tw/](http://global.msi.com.tw/)

Any other ideas? =/

(I'm about ready to go buy an IDE drive.)

---

### Post by kmolnar on 2008-08-22
I bought a new 320GB EIDE Western Digital drive, and this doesn't show up in the IDE drives list either, instead shows up simply as SCSI-1 (the other disk being SCSI-0)

I installed Ubuntu and now attempting to boot (the new EIDE drive has first boot priority) results in an "Update Success" message after the "Verifying DMI Pool Data..." message, followed by a hang. Reboots result in just the "DMI Pool" message and a hang. I can only imagine this means Ubuntu's installer has misplaced the bootloader or something, I'll poke around a bit.

UPDATE:
Couldn't get it to boot with GRUB "installed" on sdb (SCSI-1, the EIDE drive), tried this:
```

 grub> root (hd1,0)
 grub> setup (hd0)

```

and we're back to error 21. This is displayed during boot, to be precise:

```

Bus No. Device No. Func No. Vendor/Device Class Device Class                   IRQ
----------------------------------------------------------------------------------
0       26         0        8086   2834   0C03  USB 1.0/1.1 UHCI Cntrlr         10
0       26         1        8086   2835   0C03  USB 1.0/1.1 UHCI Cntrlr         10
[ ... (13 more devices listed here) ... ]
                                                ACPI Controller                  9
Verifying DMI Pool Data .............
GRUB Loading stage1.5.


GRUB Loading, please wait...
Error 21

```

(needless to say, I'm going to go return this drive)

---

### Post by kmolnar on 2008-08-23
Saw [this]("http://ubuntuforums.org/showthread.php?t=233540"), decided to give it a shot and lo and behold, GRUB loads fine... and Ubuntu boots...

...into BusyBox. So now I have a vastly different problem.

The "solution" was merely to move the drive to a different SATA port. Apparently this kicks it out of the dysfunctional JMicron RAID controller or something.

I see the Ubuntu loading screen (logo + bar) with the little patch of orange oscillating many times (never switching to the filling-up-the-bar mode) before it drops me into BusyBox with that oh-so-painful (initramfs) prompt.

Is this problem looking familiar to anyone? Should I start a new thread? Should I do any more diagnostic stuff?

Thanks in advance!

ADDENDUM:
Windows XP now boots again, also, via the GRUB entry Ubuntu added automatically.
My WD SATA drive now shows up as an "IDE" drive in the Standard CMOS Settings menu, and "LBA" is selected.
Error 21 is gone. Gone! Now I'm stuck in BusyBox. =(
Thanks to everyone who's weighed in on this so far for steering me out of a dead-end line of reasoning.

---

### Post by kmolnar on 2008-08-23
[RESOLVED!!!]

[http://ubuntuforums.org/showpost.php?p=5014592&postcount=23](http://ubuntuforums.org/showpost.php?p=5014592&postcount=23) has the final solution, and the other post had hinted at it - all-generic-ide seems to be a necessity. I'm going to go ahead and add it to my kernel options, but does anyone know the "right" place for this, in which the Debian automatic kernel business won't make me have to redo that bit every time a new kernel comes down the tubes? (EDIT: Oh, I see, just add them after "quiet splash" on the default options line, of course!)

THANKS A MILLION EVERYONE!

:popcorn: :guitar: :) :KS:KS:KS:KS:KS

---

### Post by caljohnsmith on 2008-08-23
Glad you resolved the problem, kmolnar, and thanks for posting your solution, as that will help others in the future. :)

---

