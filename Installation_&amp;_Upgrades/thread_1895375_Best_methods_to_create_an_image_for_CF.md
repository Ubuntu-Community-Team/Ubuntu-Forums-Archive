---
title: "Best methods to create an image for CF"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by gnaservicesinc on 2011-12-14
Often it seem their are more then one way to do something but one best way.  I am attempting something and I believe I have found a way  but I'm not sure if it is the best way. So what I am going to do is layout what I need to do, how I have found to do it and then if somebody knows a better way or has feedback please reply.

I am planning on installing a minimal install of Ubuntu + snort on a computer that has no hard disk drive but rather it has a compact flash card that is seen as a HDD because it connects via the IDE port. It is important that everything loads into ram because obviously the  CF over IDE is very slow. So I want to load everything into ram and not write back to the CF.

My plan is to, on my current Ubuntu desktop to follow the steps for a [customised live cd from scratch]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch") and use debootstrap to create a chroot, install everything I need and nothing more.  Then when making the iso  set up "toram" in the boot options.  Then dd the image onto the CF card.  Then when I want to update the system, I will go back into the chroot, update, and then remake the image  and then DD that onto the card. 

I have never done something like this before so I am not sure if that will work or if that is the best way to go about this.  It might even be a really BAD way to go about it, IDK that is just what I have come up with in my search. It is also possible that I am being dumb and I have missed some well know method to do this. :D

So any feedback, suggestions, links to other methods, etc will all be welcome.

Also as more background: The system that will be booting from the CF has lots of ram, 8GB, a fast 3.6Gzh quad core CPU,  and three PCI Express Intel PRO/1000 Server Adaptors (NIC cards)

Again, the goal is to make an image of a Ubuntu + Snort etc. Install that is all pre configured (The snort and networking configurations have already been created and turned into debs for easy install)  The hard part being the image needs to not write back and stay in ram for speed because not only is the CF over IDE (So thats like what 133 MByte/s.) the CF card it's self would be like 20 MByte/s) so it would be a bad idea to be writing back. 

Thanks!

---

### Post by lkraemer on 2011-12-15
Michigander,
One thing you may want to try is to use unetbootin to create your image.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Nothing else you can create your image to a USB Flash Drive, then use dd
to copy the image and move it to Compact Flash.

I've installed Tiny Core to a 2G CF and it works wonderful on my Ampro
Readyboard.  I have instructions somewhere, but I am having trouble locating
them at the moment.

Here are a few tidbits that I've stumbled across in my searches:
1.  Plug in the 2 Gig Compact Flash Card, and use Gparted to see what it mounts as.  Then create your ext2/ext3 Partition and format it.

2.  TO ZERO out a Compact Flash Card:
sudo dd if=/dev/zero of=/dev/sdb bs=16k

3.  TO ZERO out a Compact Flash Card Partition #1:
sudo dd if=/dev/zero of=/dev/sdb1 bs=16k

4.  To copy MBR simply use the dd command. dd command works under all Linux distros and other UNIX like operating systems too.
A master boot record (MBR) is the 512-byte boot sector that is the first sector of a partitioned data storage device of a hard disk.
MBR Total Size

    446 + 64 + 2 = 512

Where,

    * 446 bytes - Bootstrap.
    * 64 bytes - Partition table.
    * 2 bytes - Signature.

512 vs 446 Bytes

    * Use 446 bytes to overwrite or restore your /dev/XYZ MBR boot code only with the contents of $mbr.backup.file.
    * Use 512 bytes to overwrite or restore your /dev/XYZ the full MBR (which contains both boot code and the drive's
partition table) with the contents of $mbr.backup.file.

dd command to copy MBR (identically sized partitions only)

Type dd command as follows:
dd if=/dev/sda of=/dev/sdb bs=512 count=1
Above command will copy 512 bytes (MBR) from sda to sdb disk. This will only work if both discs have identically sized partitions.


dd command for two discs with different size partitions

# dd if=/dev/sda of=/tmp/mbrsda.bak bs=512 count=1
Now to restore the image to any sdb:
# dd if=/tmp/mbrsda.bak of=/dev/sdb bs=446 count=1
The above commands will preserve the partitioning scheme.

5.  sudo blkid
 
 udisks --mount /dev/sdb
 
 sudo umount /dev/sdb
 
 dd if=/dev/sdb of=tc30D1.img bs=1024
 dd if=/dev/sdb of=tc30D2.img bs=1024
 dd if=/dev/sdb of=tc30D3.img bs=1024
 dd if=/dev/sdb of=tc30D4.img bs=1024
 dd if=/dev/sdb of=tc30D5.img bs=1024
 
 mkdir TC30Plus_DOS/
 cd TC30Plus_DOS
 sudo mount -o loop -t msdos tc30D1.img /mnt/disk
 sudo umount /mnt/disk
 sudo mount -o loop -t msdos tc30D2.img /mnt/disk
 sudo umount /mnt/disk
 sudo mount -o loop -t msdos tc30D3.img /mnt/disk
 sudo umount /mnt/disk
 sudo mount -o loop -t msdos tc30D4.img /mnt/disk
 sudo umount /mnt/disk
 sudo mount -o loop -t msdos tc30D5.img /mnt/disk
 sudo umount /mnt/disk


I've also included some txt files I've kept over the years.  They might
give you an idea or two.

I'd think if you booted from the CDROM, and had the CF on the IDE Primary/Secondary Port, that you 
should be able to install it there.  I've done something similar with my Ampro Readyboard.  I'd recommend using
the ext2 format for the CF because it's supposed to limit the writes, if the internet is correct.  The Brand
of CF I used was Transcent, and it appears to work just fine booting Tiny Core 4.1



Larry


REF:
[http://www.damnsmalllinux.org/wiki/index.php/Frugal_Install](http://www.damnsmalllinux.org/wiki/index.php/Frugal_Install)
[http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_%28Poormans_Install%29](http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_%28Poormans_Install%29)
[http://www.knoppix.net/wiki/Poor_Mans_Install](http://www.knoppix.net/wiki/Poor_Mans_Install)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

Here is another interesting read, that you will find interesting:
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

---

