---
title: "Simplify live CD layout on flash drive"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by zoltanthegypsy on 2009-12-30
Hi all,

First-timer here.  Please point me at a more appropriate forum if there is one.

I keep a 16G flash fob on  my keychain.  Sort of a "Swiss army drive" with grub booting a customized Knoppix, Ubuntu 9.10 live CD image modified to be user-writable, Acronis, Spinrite, Memtest, and a few other tools.  Also export and scratch directories for all my personal stuff and temp file storage.

All is good.  But.  I like to keep the root dir as clean as possible, and the Ubuntu live image comes with a bunch of dirs like .disk, dists, install, pics, etc...

Is there documentation somewhere describing what all of these are for?  Better yet, ways to modify the install so all/most aren't necessary?  I've tried just renaming some of them, but that typically breaks bootability in ways I don't yet understand.

Just being fussy about this, but it might be a good learning exercise.

Thanks,
Z.

---

### Post by phillw on 2009-12-30
Hi and welcome to the Forum,

I'd leave the files & folders right where they are - the various operating systems will expect them to be in a specific place - moving them, as you have found, is a good way to break them !

As you asked for more information on how / why / what they are, I'll send you over to this  How To --> [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)  It explains what is what & why it is there. Just be aware, it's quite involved !!!

Regards,

Phill.

---

### Post by zoltanthegypsy on 2009-12-30
Thanks Phill.

That was quick!  I'll have a look at Live CD customization.  I did a fair bit of that back in the Knoppix 4.x and 5.x days getting things like NTFS support to work.  It will be interesting to see how it's done these days in Ubuntu land.

Thanks again,
Z.

---

### Post by Matt Yun on 2009-12-30
> **zoltanthegypsy said:**
> 
I keep a 16G flash fob on  my keychain.  Sort of a "Swiss army drive" with grub booting a customized Knoppix, Ubuntu 9.10 live CD image modified to be user-writable, Acronis, Spinrite, Memtest, and a few other tools.  Also export and scratch directories for all my personal stuff and temp file storage.


I also have a 16GB "Swiss army drive", but with SLAX, BackTrack 3, and Tiny Core and a bunch of Windows portable apps.  Just out of curiosity, may you post your menu.lst?

Also, what filesystem do you use?  I had to split my drive into two partitions, FAT32 for the Windows-readable partition, and a 4GB Ext2 partition for SLAX.

---

### Post by zoltanthegypsy on 2009-12-30
> **Matt Yun said:**
> I also have a 16GB "Swiss army drive", but with SLAX, BackTrack 3, and Tiny Core and a bunch of Windows portable apps.  Just out of curiosity, may you post your menu.lst?

Also, what filesystem do you use?  I had to split my drive into two partitions, FAT32 for the Windows-readable partition, and a 4GB Ext2 partition for SLAX.

I use one big FAT32 partition.  That's why I use live CD images instead of more sane flash installs.  The live stuff can live in a FAT32 partition and doesn't require that it be a big EXT2 or 3 or whatever partition, or multiple partitions.

This thing gets used for salvaging Win boxen (not by me much, but I gave a copy to a friend who does it in his line of work, and has the appropriate licenses) and to save ongoing backups of files I fiddle on my Win box.  FAT32 is pretty much required for this, and WinXX will only mount the first partition on a flash drive so multiple partitions don't work well.

As to menu.lst, it's quite a mess since it's left over from my original Knoppix fiddling, but here it is (BEEZIX is my modded Knoppix, the others are self-explanatory -- beware line-wrapping!):

# menu.lst for BEEZIX 5.1.1B0.1 installation on USB thumb drive

default=0
timeout=10
splashimage=(hd0,0)/boot/grub/bootsplash.xpm.gz

title BEEZIX 5.1.1B0.1 X DMA
    root (hd0,0)
    kernel /boot/isolinux/linux ramdisk_size=100000 init=/etc/init apm=power-off vga=791 nomce dma lang=us
    initrd /boot/isolinux/minirt.gz

title BEEZIX 5.1.1B0.1 X NO DMA
    root (hd0,0)
    kernel /boot/isolinux/linux ramdisk_size=100000 init=/etc/init apm=power-off vga=791 nomce nodma lang=us
    initrd /boot/isolinux/minirt.gz

title BEEZIX 5.1.1B0.1 CMD LINE
    root (hd0,0)
    kernel /boot/isolinux/linux ramdisk_size=100000 init=/etc/init apm=power-off vga=791 nomce 2 lang=us
    initrd /boot/isolinux/minirt.gz

title BEEZIX 5.1.1B0.1 X NO DHCP
    root (hd0,0)
    kernel /boot/isolinux/linux ramdisk_size=100000 init=/etc/init apm=power-off vga=791 nomce nodhcp lang=us
    initrd /boot/isolinux/minirt.gz

title BEEZIX 5.1.1B0.1 FAILSAFE
    root (hd0,0)
    kernel /boot/isolinux/linux ramdisk_size=100000 init=/etc/init vga=normal atapicd nosound noapic noacpi pnpbios=off acpi=off nofstab noscsi nodma noapm nousb nopcmcia nofirewire noagp nomce nodhcp xmodule=vesa lang=us
    initrd /boot/isolinux/minirt.gz

title WINDOWS MAYBE!!!!!
    map (hd0) (hd1)
    map (hd1) (hd0)
    rootnoverify (hd1,0)
    makeactive
    chainloader +1

title Ubuntu 9.10 32 Bit "live CD"
    kernel /casper/vmlinuz file=/preseed/ubuntu.seed boot=casper ramdisk_size=1048576 root=/dev/ram rw basemountmode=rw,noatime,uid=999,gid=999
    initrd=/casper/initrd.lz

title Acornix 2010 Recovery CD
    kernel /acornix/kernel.dat vga=0x314 ramdisk_size=40000 quiet
    initrd=/acornix/ramdisk_merged.dat

title SpinWrong 6.0
    kernel /boot/isolinux/memdisk
    initrd=/boot/isolinux/SpinRite.img

title MEMTEST
    root (hd0,0)
    kernel /boot/isolinux/memtest

---

