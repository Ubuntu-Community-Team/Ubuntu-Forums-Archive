---
title: "GPARTED resize and move nightmare - [PLEASE HELP]"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by rmp73 on 2010-06-25
Can you please help?  I'm not a total novice, but I'm a relative noob, particularly when it comes to Linux command line syntax etc.

I've a 200GB HDD in my Vaio laptop, which had 3 partitions on it:
sda1 ext4 /root Ubuntu 10.04 - 10GB
sda2 ext4 /home data files   - approx 186GB
sda3 swap                    - 2.5GB

As I wanted to update my iPhone to iOS4, which requires iTunes 9.3 and that won't run in VirtualBox and I was having a mare getting VMWare installed for some reason, I decided yesterday to 'resize and move' my /home partition to create a 30GB partition for Windows 7 on partition 2 (I saw a post recommending it follow /dev/sda1 for ease of GRUB setup or something similar).

So, I created a GPARTED LiveDisk USB and kicked off the process of 'resizing and moving' the partition /dev/sda2 and creating a /dev/sda3 partition formatted to NTFS.  NOTE: I did not read anywhere (beforehand) that I needed to 'disable swap' so I didn't - in case that's of any importance here.

When I got up this morning, I saw error messages on the GPARTED screen and something telling me that the errors had been saved to a .htm file somewhere, which at 4.30am I forgot to note down as I had a 4-hour drive ahead of me.

Suffice to say, something went wrong with the reduction of the partition and its subsequent move (during the move, I believe).  I've managed to restart the laptop (in recovery mode I think) and I'm at the command line after receiving an error about not being able to mount (sda2 where /home was) a partition, which I chose to 'manually fix/mount' and received this command line prompt text:

**starts**
Filesystem check or mount failed;
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored
**ends**

First of all, I ran this lot:

**starts**
root@ryan-laptop:~# fsck
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1 is mounted.

WARNING!!! The filesystem is mounted.  If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 45562348 blocks
The physical size of the device is 37698530 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

root@ryan-laptop:~# fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1 is mounted.

WARNING!!! The filesystem is mounted.  If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

root@ryan-laptop:~# fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 45562348 blocks
The physical size of the device is 37698530 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

root@ryan-laptop:~# fsck /dev/sda3
fsck from util-linux-ng 2.17.2
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda3

root@ryan-laptop:~# fsck /dev/sda4
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
**ends**    

(Out of curiosity, I tried /dev/sda5 for fun and got the same response as per /dev/sda4)

so then I ran fdisk - l and here's the output:

**starts**
root@ryan-laptop:~# fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units - cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002e822

    Device Boot     Start      End       Blocks    Id  System
/dev/sda1    *          1     1305     10482381    83  Linux
/dev/sda2            5222    23994    150794122+   83  Linux
/dev/sda3           23995    24321      2626627    82  Linux swap / Solaris
**ends**

Now, to me, that kind of looks like there's a gap where the new NTFS partition should be (1306 to 5221).

What the heck should I do?  Restart the laptop from the GPARTED LiveDisk USB and create a new partition table?  If so, with the old values (sda1 10733 / ext4, sda2 186623 /home ext4, sda3 2689 swap) or new values (sda1 10733 / ext4, sda2 32212 /ntfs, sda3 154411 /home ext4, sda3 2689 swap)... part of my issue is the various programs and data conversion calculators use different values for the size of a partition (10GB, 10733, etc. for the same thing)

Please can you advise?

---

### Post by darkod on 2010-06-25
Why do you rely only on Gparted Livedisc? Boot the ubuntu cd in live mode (so it doesn't mount / and doesn't try to mount /home), and from there run:

sudo fsck /dev/sda2

to check sda2 after the resize.
Also in live mode you can also use Gparted in System-Administration and if there really is confirmed gap of unallocated space, simply create ntfs partition from it. Why new partition table?

But first do the fsck on sda2 to see what it says.

---

### Post by rmp73 on 2010-06-25
> **darkod said:**
> Why do you rely only on Gparted Livedisc? Boot the ubuntu cd in live mode (so it doesn't mount / and doesn't try to mount /home), and from there run:

sudo fsck /dev/sda2

to check sda2 after the resize.
Also in live mode you can also use Gparted in System-Administration and if there really is confirmed gap of unallocated space, simply create ntfs partition from it. Why new partition table?

But first do the fsck on sda2 to see what it says.

So this might sound obvious, but I don't appear to have sudo rights when I launch the live session...  When I pulled up a terminal, here's what happpened:

**starts**
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
>>> /etc/sudoers: syntax error near line 43 <<<
sudo: parse error in /etc/sudoers near line 43
sudo: no valid sudoers sources found, quitting
**ends**

Thoughts?

---

### Post by darkod on 2010-06-25
Actually I haven't seen that for live mode. :(

Try getting a root shell first with sudo -i:

sudo -i
fsck /dev/sda2

If it still shows the same error, can the cd/image file be corrupted?

---

### Post by rmp73 on 2010-06-25
> **darkod said:**
> Actually I haven't seen that for live mode. :(

Try getting a root shell first with sudo -i:

sudo -i
fsck /dev/sda2

If it still shows the same error, can the cd/image file be corrupted?

OK, for the moment, I'm seeking an alternative to running the command in the terminal as I've the issue above and it's not resolved.

Instead, I've attached a couple of screen shots for you - I've launched >System >Admin >Disk Utility and this is what I see for the HDD: (screenshot1.png)
[ATTACH]161518[/ATTACH]

When I try to mount the /dev/sda2 partition, I receive (screenshot2.png) with the error
"Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[IMG]file:///tmp/moz-screenshot.jpg[/IMG]"
[ATTACH]161519[/ATTACH]

---

### Post by darkod on 2010-06-25
I just remembered that Gparted can also run checks. What happens if you boot in live mode, open Gparted and right-click /dev/sda2 and select Check?

Otherwise, the disk utility looks fine, it shows unallocated space created. But it seems the resize and move process was not finished all the way trough for sda2.

---

### Post by rmp73 on 2010-06-25
> **darkod said:**
> I just remembered that Gparted can also run checks. What happens if you boot in live mode, open Gparted and right-click /dev/sda2 and select Check?

Otherwise, the disk utility looks fine, it shows unallocated space created. But it seems the resize and move process was not finished all the way trough for sda2.

When I access >System >Administration >Gparted, it doesn't appear to run... A box comes up on the status bar, which reads "Starting Gparted" but after about 10 seconds it disappears.  Could this be because Ubuntu doesn't have the right version of syslinux installed?  A post I read yesterday here: [http://www.moosechips.com/2009/05/bootable-gparted-usb-stick/](http://www.moosechips.com/2009/05/bootable-gparted-usb-stick/) stated I needed a more current version of syslinux for Gparted to work... that would appear to hold true as the USB wouldn't load properly without it.

---

### Post by rmp73 on 2010-06-25
> **darkod said:**
> I just remembered that Gparted can also run checks. What happens if you boot in live mode, open Gparted and right-click /dev/sda2 and select Check?

Otherwise, the disk utility looks fine, it shows unallocated space created. But it seems the resize and move process was not finished all the way trough for sda2.

There is an option in the Disk Utility application to "Check Filesystem".  When I click on /dev/sda2 and click that option, I receive a pop up box that reads: File system check on "154 GB Filesystem" (Partition 2 of ATA FUJITSU MHV2200BT) completed - File system is NOT clean.

---

### Post by darkod on 2010-06-25
> **rmp73 said:**
> When I access >System >Administration >Gparted, it doesn't appear to run... A box comes up on the status bar, which reads "Starting Gparted" but after about 10 seconds it disappears.  Could this be because Ubuntu doesn't have the right version of syslinux installed?  A post I read yesterday here: [http://www.moosechips.com/2009/05/bootable-gparted-usb-stick/](http://www.moosechips.com/2009/05/bootable-gparted-usb-stick/) stated I needed a more current version of syslinux for Gparted to work... that would appear to hold true as the USB wouldn't load properly without it.

It might be related also to not allowing sudo. After all, Gparted also requires sudo permissions.
If you suspect the usb stick is not fully operational, try creating it on another ubuntu computer if possible, just look in System-Administration for Startup Disc Creator.
If you don't have another ubuntu computer, you can also use in windows unetbootin instead of the universal usb installer recommended on ubuntu.com to create the live usb stick.

It seems Disk Utility doesn't try to fix it, it just scanned it. But at least now you know what the issue is for sure, the FS is not clean on sda2.
Try recreating the live usb stick and go back to the original suggestion:
sudo fsck /dev/sda2

---

### Post by rmp73 on 2010-06-25
> **darkod said:**
> It might be related also to not allowing sudo. After all, Gparted also requires sudo permissions.
If you suspect the usb stick is not fully operational, try creating it on another ubuntu computer if possible, just look in System-Administration for Startup Disc Creator.
If you don't have another ubuntu computer, you can also use in windows unetbootin instead of the universal usb installer recommended on ubuntu.com to create the live usb stick.

It seems Disk Utility doesn't try to fix it, it just scanned it. But at least now you know what the issue is for sure, the FS is not clean on sda2.
Try recreating the live usb stick and go back to the original suggestion:
sudo fsck /dev/sda2

If you can stick with me a bit longer Darkod I'd be really grateful.  I shall try to do what you suggest, BUT, I'm working now at my holiday home, where we have a 0.5Mb Internet connection so downloading anything new is out of the question.  I have a second PC with me, BUT it has USB encryption s/w running so I can't plug in my external 1.5TB HDD where I "think" I have a backup of the 10.04 ISO... If I don't have it there, it's on the 'corrupted?' /dev/sda2 in my /home/Downloads folder... Argh.

Is there a way to check if the USB I'm using is corrupt?  I don't think it is, but I do keep receiving "Low Disk Space" messages.  It's a 2GB USB stick... (Just looking at it, could I delete the directory that's on there called /rofs - as it's taking up 1.7GB!!!!

---

### Post by darkod on 2010-06-25
I don't know how you created the usb stick, but more and more it sounds like that is your issue. It shouldn't complain about low space unless you are actually booting the ISO directly, in which case it needs space to unpack it and run it.
That's the thing, you can boot it in few different ways.
The Startup Disc tool in ubuntu, and unetbootin, unpack the ISO and create boot files so you can boot from the usb stick. As long as you have 700MB free on the stick before this procedure, it should be fine because that's all the ISO takes.

Another idea: I wonder if recovery mode can help. Just select ubuntu to boot in the recovery mode entry, not the normal mode. In case you don't get boot menu, start hitting Shift when you boot to show the menu.
After you select the recovery mode, select something like "root with networking" to have internet access just in case.
It might or might not mount /dev/sda2 as /home. Even if it does, unmount it with:

umount /dev/sda2 (it's not a typo, the command is umount)

Then try the:

fsck /dev/sda2

In this case you are already at root prompt so sudo shouldn't be needed.

---

### Post by rmp73 on 2010-06-25
> **darkod said:**
> I don't know how you created the usb stick, but more and more it sounds like that is your issue. It shouldn't complain about low space unless you are actually booting the ISO directly, in which case it needs space to unpack it and run it.
That's the thing, you can boot it in few different ways.
The Startup Disc tool in ubuntu, and unetbootin, unpack the ISO and create boot files so you can boot from the usb stick. As long as you have 700MB free on the stick before this procedure, it should be fine because that's all the ISO takes.

Another idea: I wonder if recovery mode can help. Just select ubuntu to boot in the recovery mode entry, not the normal mode. In case you don't get boot menu, start hitting Shift when you boot to show the menu.
After you select the recovery mode, select something like "root with networking" to have internet access just in case.
It might or might not mount /dev/sda2 as /home. Even if it does, unmount it with:

umount /dev/sda2 (it's not a typo, the command is umount)

Then try the:

fsck /dev/sda2

In this case you are already at root prompt so sudo shouldn't be needed.

Regarding the USB stick, I used the feature built into the OS for creating a USB stick...

As you were typing, I went back to the drawing board and pretty much did what you suggested - here are the results:

Switch on PC
Hold down Left Shift
Choose Ubuntu, with Linux 2.6.32-23-generic (recovery mode)

**starts**
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
[  14.766337] uvcvideo: Failed to query (129) UVC probe control : -32 (exp.26)
[  14.766439] uvcvideo: Failed to initialize the device (-5)
/dev/sda1: clean, 190748/655360 files, 1122012/2620595 blocks
/dev/sda2: The filesystem size (according to the superblock) is 45562348 blocks
The physical size of the device is 37698530 blocks
Either the superblock or the partition table is likely to be corrupt!

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
   (i.e., without -a or -p options)
mountall: fsck /home [420] terminated with status 4
mountall: Filesystem has errors: /home
**ends**

At this point, if I press 'Esc' or any other key, the Ubuntu splash appears but there's no more HDD activity so I hit reboot and let it start without any interference from me

Splash screen appears with:
**starts**
Errors were found while checking the disk drive for /home

Press F to attempt to fix the errors, I to ignore, S to skip mounting or M for manual recovery
**ends**

Hit M

**starts**
Filesystem check or mount failed;
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored
root@ryan-laptop:~# 
**ends**

So then I try running fsck manually

**starts**
root@ryan-laptop:~# fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 45562348 blocks
The physical size of the device is 37698530 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

/dev/sda2 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structures
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Errorreading block 37748736 (Invalid argument) while reading inode and block bitmaps. Ignore error<y>? no

fsck.ext4: Can't read an block bitmap while retrying to read bitmaps for /dev/sda2
e2fsck: aborted
**ends**

Try running it with Ignore error = Y

**starts**
Force rewrite<y>?
**ends**

What shall I do...?

---

### Post by rmp73 on 2010-06-25
Oh, and if I hit 'S' to skip mounting, I arrive at the log in screen and see my username (ryan) and 'other' underneath... Logging in as me returns one error after another and I end up going nowhere and rebooting.

---

### Post by darkod on 2010-06-25
Sorry, I don't know this much about fsck and these errors. :(
If it doesn't repair them automatically, I have no idea which options to choose. Or if another tool like testdisk for example can help.

---

### Post by rmp73 on 2010-06-25
> **darkod said:**
> Sorry, I don't know this much about fsck and these errors. :(
If it doesn't repair them automatically, I have no idea which options to choose. Or if another tool like testdisk for example can help.

Righto Darkod. Thanks for ALL your help to this point...

Would you happen to know how to access sdb1 from a command line so I can 'delete' the 'rofs' directory and all its contents as they seem to be a duplicate of the OS (persistent profile perhaps) as it's kept expanding and now I can't use the USB stick anymore until I clear some space on it...

---

### Post by darkod on 2010-06-25
From command line it should be:

sudo mount /dev/sdb1 /mnt
cd /mnt
ls

should list all files/folder inside. Just remember the mount point is /mnt and that's the starting point, the root.

From live mode you should be able to see it in Places but I'm not sure what will it allow to delete if you are actually booted from it.
That's why I never create them with persistency. :)

---

### Post by rmp73 on 2010-06-25
> **darkod said:**
> From command line it should be:

sudo mount /dev/sdb1 /mnt
cd /mnt
ls

should list all files/folder inside. Just remember the mount point is /mnt and that's the starting point, the root.

From live mode you should be able to see it in Places but I'm not sure what will it allow to delete if you are actually booted from it.
That's why I never create them with persistency. :)

I've asked my other half to pick up a 4GB USB stick whilst she's out, was thinking I could boot from the existing one and create a new one... Only thing is, I fear the existing one won't now let me boot any more unless I can clear some stuff off it... (argh!)

---

### Post by rmp73 on 2010-06-25
Bump

---

### Post by darkod on 2010-06-25
Sorry, no new ideas. Did you manage to mount the stick and get rid of something to clear space? As per my last post.

---

### Post by rmp73 on 2010-06-25
I tried... But then, it's dangerous deleting files when you're not ENTIRELY certain what they do... I now have a brand new 4GB USB Flash drive but I need to create a Ubuntu Live Disk on a MAC as the work PC is encrypting USB disks and I seem to have frigged something on the existing Live USB whilst trying to reduce the clutter... Not having a lot of fun here!

---

### Post by rmp73 on 2010-06-25
Phew, what a relief.  Thanks to someone who pointed out that Testdisk might be an option. I restarted the machine using the Gparted Live USB stick and once the partition table appeared, I cancelled that, clicked on Terminal and typed in Testdisk... to my astonishment and great relief, I indeed found the application ran and after following a few prompts (option A on the list I believe) it found my old partitions, I selected the option to accept proposed changes or something similar and it basically restored the partition table to the state it was in yesterday before I started the whole fiasco of resizing and moving the partition. I was able to reboot the PC, allowed Ubuntu to 'fix' the errors it found during startup and once again find myself with a working laptop... phew!  

I've taken the opportunity to back up my entire /home partition and tomorrow, after some sleep, I'll revisit how best to create a partition for Windows 7.

Suggestions welcome.  Should I a) shrink the ext4 partition that has spare room and create a new partition to the right of it in the partition table, or simply remove the existing partitions /dev/sda2 and 3 (/home and /swap) creating one big unallocated space to the right of /dev/sda1 (/ root0....?

---

### Post by darkod on 2010-06-25
At least you got it back now. :) Maybe we should have tried testdisk much earlier.

If you delete /home and swap and recreate them later, you would have to go into /etc/fstab to make ubuntu use them again with the new UUIDs. I have never tried to do that.

You could try to resize /dev/sda2 again but this time leave the empty space after it, to the right. Just drag the end to the left. In that case it moves only data if necessary, but doesn't move the whole partition to the left.
It should be a much faster process, especially if you have little data in the last 30GB that you want to shrink.

Both option carry some risk.

---

### Post by rmp73 on 2010-06-26
> **darkod said:**
> At least you got it back now. :) Maybe we should have tried testdisk much earlier.

If you delete /home and swap and recreate them later, you would have to go into /etc/fstab to make ubuntu use them again with the new UUIDs. I have never tried to do that.

You could try to resize /dev/sda2 again but this time leave the empty space after it, to the right. Just drag the end to the left. In that case it moves only data if necessary, but doesn't move the whole partition to the left.
It should be a much faster process, especially if you have little data in the last 30GB that you want to shrink.

Both option carry some risk.

The first thing I did when the data came back was copy all 70-odd GB to the external HDD.  That was successful.

Today, I thought I'd start by recreating the Live Ubuntu USB stick.  Oddly, in Nautilus I can't see ANY of the content on it, though there's stuff there, given the volume file size information etc.  Similarly, when I mount the 10.04 image on the HDD, there too, I can't see any of the content. Perhaps the data on /dev/sda2 is corrupted?  I might try rebooting from the GPARTED USB again and running testdisk over the data and see what it throws up... Unless you have any other thoughts?

As time goes by I'm realizing a number of files or directories may have been corrupted by the failed GPARTED resize and move that I was trying to perform.  It appears large files are particularly prone - VirtualBox VDIs aren't working and that 10.04 ISO for example. However, a 2GB Truecrypt container file seems OK.

I think I'm going to have to delete my /dev/sda2 (/home) and /dev/sda3 (swap) partitions and then create new partitions /dev/sda2 30GB NTFS /dev/sda3 (/home) ?? whatever space is left after adding /dev/sda4 (Linux Swap)...

---

