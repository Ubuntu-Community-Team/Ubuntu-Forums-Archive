---
title: "Problem installling Edgy using HDD method."
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Fataltragedy2 on 2007-03-15
Hello,

I'm trying to install ubuntu using the 'Install from .ISO' method.

I followed all the steps, created partitions. Installed GRUB.

Appended the information to the MENU.LST and placed the vlinuz and intrd.gz with the .ISO in a /boot folder within a seperate partition.

Upon restart, Grub loads fine and dandy. I get the 'Install Ubuntu' function, but upon pressing enter it says:

Error hd(0,3)
Partition does not exist.

Can anyone help me with this?

I've currently got 4 true logical partitions on my HDD, A memory stick drive, two DVD drives (One is virtual for mounts.) The boot files are in my 4th true logical partition, and counting CD drives it's somewhere around the 6th.

Where am I going wrong? Does GRUB count CD drives too?

---

### Post by thingy on 2007-03-15
Grub does not count CDROM drives.

Please ensure you don't have any SD/MMC/etc cards in the card reader drive and the error message you mention indicates that grub is looking at the wrong partition.

Currently you are instructing grub to look at drive 0, 4th partition (i.e. first extended partition) for the kernel.

Is that the partition with the /boot files?

What are the 4 partitions in your hard drive?

---

### Post by Fataltragedy2 on 2007-03-15
Thank you for your reply!

I've currently got 4 true partitions.

C: D: H: and I: (The rest are various random mount drives etc.)

I: is the one which contains the /boot/ directory containing vmlinuz (1538KB) initrd.gz (1570KB) and the ISO.

When I use (0,3) as the source, a partition isn't detected. When I counted CD-Drives and put in (0,6) It detected an NTFS drive, but it gave an error saying the files could not be found.

---

### Post by thingy on 2007-03-15
Ok the drive letters don't tell us how you are partitioned.

I will have to make assumptions!

Assumption 1. C: = Primary parititon (hd0,0)

Assumption 2. D: = Logical parition (hd0, 4)  (4 == the first extended partition)


umm I just realized that you said your I: drive is an NTFS file system.

According to the grub howto: [http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

> Support multiple filesystem typesSupport multiple filesystem types transparently, plus a useful explicit blocklist notation. The currently supported filesystem types are BSD FFS, DOS FAT16 and FAT32, Minix fs, Linux ext2fs, ReiserFS, JFS, XFS, and VSTa fs. See [Filesystem]("http://www.gnu.org/software/grub/manual/html_node/Filesystem.html#Filesystem"), for more information.       


Change the I: to a FAT32. To do this, copy its files to C: for example, format I: as FAT32 and copy your files back. Take care when formatting. Your doing this at your own risk!!!


Oh and btw, your hd0,6 is the right syntax to specify the I: drive!

---

### Post by Fataltragedy2 on 2007-03-15
I used (0,4) and it began loading (I think grub considers my card reader as a partition. It came preinstalled with my VAIO laptop.)

Anyhows, I've encountered yet another problem. The kernel starts loading and then it stops.

It says

Kernal panic: Cannot load onto boot (0,0) or something similar. What could be causing this?

---

### Post by thingy on 2007-03-15
Paste the grub.conf or menu.lst file you modified so that we can see what you have setup.

Also, i don't think the card reader would pop up as a parition. It might pop up as a hard drive i.e.

hd1,0

So when you are specifying hd0,4 you are telling grub to look at D: drive if the assumptions i made about your partitioning scheme are correct.

---

### Post by Fataltragedy2 on 2007-03-15
title Install Ubuntu
root (hd0,4)
kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /boot/initrd.gz

That's in my menu.lst (Grub is installed on my C: drive.)

Also, my D: drive doesn't contain the vmlinuz kernel so how would it load :S It doesn't even have a boot directory.

Now when I launch grub, it stops and gives me that Kernal panic error, so SOMETHING is working, but something is wrong too.

(I used CoLinux on windows yesterday and it gave me the same error I think, if that helps.)

---

### Post by Fataltragedy2 on 2007-03-15
And here's a screenshot of my partitioning, if this helps.

[img]http://img260.imageshack.us/img260/6158/ubuntufj0.jpg[/img]

THANKS.

---

### Post by Fataltragedy2 on 2007-03-15
I'm restarting now to get the exact error I'm getting so I can post it here!

---

### Post by thingy on 2007-03-15
The screen shot did help!

Doh! My assumptions were wrong. Your drive lettering was misleading. Oh well!

Your I: is indeed the first extended partition! so hd0,4 is the correct syntax for specifying the i: drive.

hmm so the kernel is loading fine and it can't find ramdisk or it finds the ramdisk but cant find the iso...hmm i dont know whats going on until we see the error message you get.

---

### Post by Fataltragedy2 on 2007-03-15
Okay, here's  what happens after the Kernel starts loading.

RAMDISK - Compressed image found on Block 0
RAMDISK - Ran out of compressed data.

Invalid compressed format (err=1)

VFS: Cannot open root device 'rd/0' on unknown block (0,0)

Please append a correct 'root=' boot option.

Kernal panic - not syncing. Unable to mount root fs on block (0,0)

---

### Post by thingy on 2007-03-15
checksum the initrd.gz file youve got against the location you downloaded it from. Sometimes web browsers will treat .gz files specially.

---

### Post by Fataltragedy2 on 2007-03-15
> **thingy said:**
> checksum the initrd.gz file youve got against the location you downloaded it from. Sometimes web browsers will treat .gz files specially.

Hmm, I'm using the md5 checksum right now, one thing that is obvious is the filesize difference, on the site i'm getting it from it's 4.2MB

The file i've got is 1.5MB

The md5's are completely different.

I'm now restarting to see if anything has changed.

---

### Post by thingy on 2007-03-15
I assume you are following a guide like this:

[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

Anyway if the file sizes are different then you just need to re-download the files and then continue with the guide. Remember it says that the install WILL fail to find the ISO file since you need to do a manual step to point it to the right place.

good luck

---

### Post by Fataltragedy2 on 2007-03-15
Okay, It ran smoothly this time. However there's (YET ANOTHER :p) Problem now. It failed to detect the ISO (which it said it would.) I ran busybox (Ctrl+Alt+F2) and typed in

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

It accepted both commands.

Upon pressing Ctrl+alt+F1 and searching for the ISO again, it didn't find it :( Helllp :(

(Also, it completely fudged my Keyboard layout [0 button wasn't working and was trying some weird comma things instead, so I had to num lock and use the keypad.)

---

### Post by zvacet on 2007-03-16
From your screenshot I can see that your Ubuntu is ntfs format.Ubuntu use ext3.

---

### Post by thingy on 2007-03-16
> **zvacet said:**
> From your screenshot I can see that your Ubuntu is ntfs format.Ubuntu use ext3.

Its weird that grub finds the kernel + ramdisk image from the NTFS I: drive!

Anyway, see this thread (its pretty long) and in it people are reporting the same issue as you.

[http://www.ubuntuforums.org/showthread.php?t=316093&page=2](http://www.ubuntuforums.org/showthread.php?t=316093&page=2)

Can you confirm you are using the alternate iso and not a desktop one?

There is a bug report filed for it, and the fix seems to be to use the alternate install cd.

[https://launchpad.net/ubuntu/+source/busybox/+bug/66220](https://launchpad.net/ubuntu/+source/busybox/+bug/66220)

---

