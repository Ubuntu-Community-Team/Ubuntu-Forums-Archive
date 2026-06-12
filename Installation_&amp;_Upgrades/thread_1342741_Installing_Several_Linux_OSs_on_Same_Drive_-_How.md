---
title: "Installing Several Linux OSs on Same Drive - How?"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by booksnmore4you on 2009-12-01
I am pulling my hair out, for three freaking days now, trying to install several Linux OS's, including Ubuntu and Xubuntu, on the same drive.  

I don't have Windows installed and don't wish to have it, although by now the option is looking quite attractive.

While I find plenty of very long-winded blog-dissertations about the  technical minutia of Linux drives, I can't find any plain how-to's.  Sheesh.  Who beyond one-tenth of one percent of computer users is the intended audience for these?

So far, I have partitioned my drive with Gparted two different ways and experience problems.  

One, I have created a main ext4 drive for /boot, another main for swap, and another main drive with several ext4 extension drives for / (root).  *Problem:* when I install a second Linux OS into /boot, the first does not boot from grub, although the second installation is listed.  *The same OS, the second one installed, boots from either drive.  *This is so whether I format /boot anew or not.  

Two, as you can see from the results of [FONT=Fixedsys][COLOR=Green]sudo fdisk -l[/COLOR][/FONT], I have created what you see here:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    5  Extended
/dev/sda5               1          65      522049+  83  Linux
/dev/sda6           19335       19595     2096451   82  Linux swap / Solaris
/dev/sda7              66        6439    51199123+  83  Linux
/dev/sda8            6440       12861    51584683+  83  Linux
/dev/sda9           12862       19334    51994341   83  Linux
/dev/sda10          19596       25969    51199123+  83  Linux
/dev/sda11          25970       32441    51986308+  83  Linux
/dev/sda12          32442       38913    51986308+  83  Linux

Partition table entries are not in disk order
```[I]

Problem with the above:[/I] when I install a second Linux OS into sda1, /boot, and sda7, / (root), the first does not boot from grub, although the second installation *is* listed.  *The same OS**, the second one installed, ** boots from either drive.  *This is so whether I format /boot anew or not, or install the second /boot to another drive.

Also, with two, when I install everything of the second OS into the second extension drive, and nothing new into the dedicated boot partition into which the first OS has been installed, the second OS also boots from either drive listed in grub - the first, appears to exist on the drive, and is listed in grub like I said, but the same OS boots irrespective of the drive from which I boot.

I hope I'm remembering the above details correctly.  But this all is simply ridiculous.

I cannot possibly be the first person to have tried to do multiple Linux OSs on the same drive, but I am utterly frustrated trying to find a **plain how-to** on how to do it successfully.  I am no noob by any means but don't have a degree in computer science or programming and don't want to have one.   I don't wish to spend the bulk of my life underneath the hood of my system! [B]Three freaking days now!  36 hours, by now!  Down the drain!!

[/B] Please, HELP!!!  How do I partition my drive and install the numerous OSs so each works and does not wipe out the other?

---

### Post by louieb on 2009-12-01
Don't use the same  /boot with multiple Linux Distributions - been there done that - what a disaster.  (sharing swap works well).  

Use one of your partitions as a dedicated GRUB partition.  [IDBS make a dedicated GRUB partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")

And chainload to your Linux install(s) from it. 

The only thing your have to do different - when you install a Linux distribution make sure you tell the installer to put GRUB in the _**boot sector **_of its / (root) partition.   

The menu.lst in the dedicated GRUB partition would look something like this (using grub legacy - if you use GRUB2 it would be different)
```
title chainload linux in sda2
root (hd0,1)
chainloader +1

title chainload linux in sda3
root (hd0,2)
chainloader +1

title chainload linux in sda5
root (hd0,4)
chainloader +1

title chainload linux in sda6
root (hd0,5)
chainloader +1

title lol more and more lol
....
```

---

### Post by tommcd on 2009-12-01
I routinely boot several distros on my desktop and laptop with no problems. Here is what I do:
I have never used a separate boot partition. It is not needed, and as Louieb said, it can cause problems. I have also never used a separate grub partition.
 I create a separate partition for each distro's root partition. I also make a swap partition, which all the distros share. You can share swap between 32 bit and 64 bit distros with no problems. I also have a **/data** partition for my personal data that all distros share. This way each distro's home directory is contained within each distro's root partition. This keeps all those hidden .config files and folders in home separated so one distro's config files can't conflict with the other distros config files.

For booting, I install Ubuntu's grub to the MBR. This is just my preference. You could install another distro's grub to the MBR if you wish. With grub2 in Ubuntu 9.10 I boot all my distros directly from grub2 installed to the MBR.
When you install other distros, either elect not to install a boot loader, or install that distros boot loader to it's boot sector as Louieb suggested. Then just run **sudo update-grub** from Ubuntu 9.10 to update grub and add that distro to Ubuntu 9.10's grub2 boot menu. This should work fine in most cases. If grub2 fails to detect one of your distros for some reason, you can create a custom entry for that distro in grub2 as per this tutorial from the wiki:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
The part about custom entries in grub2 is here:
[https://wiki.ubuntu.com/Grub2#User-defined Entries](https://wiki.ubuntu.com/Grub2#User-defined Entries)
I had to create a custom entry in grub2 for my 64 bit Slackware 13. For some reason grub2 automatically detected 32 bit Slackware, but would not detect 64 bit Slackware.
Hope this helps.

---

### Post by booksnmore4you on 2009-12-01
I appreciate the replies.

I'm already at a snag.

The how-tos state to edit [FONT=Bitstream Vera Sans Mono]menu.lst[/FONT] in the grub folder - "/boot/grub/menu.lst is the exact file path and filename of the configfile for GRUB to load."   

No such animal. Here's the complete list of files in /boot folder.

/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/915resolution.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/acpi.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/affs.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/afs.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/afs_be.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/aout.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/ata.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/ata_pthru.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/at_keyboard.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/befs.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/befs_be.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/biosdisk.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/bitmap.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/blocklist.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/boot.img
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/boot.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/bsd.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/bufio.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/cat.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/cdboot.img
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/chain.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/cmp.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/command.lst
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/configfile.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/core.img
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/cpio.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/cpuid.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/crc.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/date.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/datehook.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/datetime.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/device.map
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/diskboot.img
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/dm_nv.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/drivemap.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/echo.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/efiemu.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/efiemu32.o
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/efiemu64.o
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/elf.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/ext2.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/extcmd.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/fat.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/font.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/fs.lst
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/fs_file.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/fshelp.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/fs_uuid.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/gfxterm.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/gptsync.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/grub.cfg
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/grubenv
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/gzio.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/halt.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/handler.lst
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/handler.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/hdparm.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/hello.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/help.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/hexdump.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/hfs.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/hfsplus.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/iso9660.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/jfs.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/jpeg.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/kernel.img
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/keystatus.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/linux.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/linux16.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/lnxboot.img
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/loadenv.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/loopback.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/ls.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/lsmmap.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/lspci.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/lvm.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/mdraid.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/memdisk.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/memrw.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/minicmd.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/minix.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/mmap.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/moddep.lst
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/msdospart.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/multiboot.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/normal.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/ntfs.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/ntfscomp.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/ohci.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/part_acorn.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/part_amiga.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/part_apple.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/part_gpt.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/partmap.lst
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/part_msdos.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/part_sun.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/parttool.lst
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/parttool.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/password.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/pci.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/play.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/png.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/probe.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/pxe.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/pxeboot.img
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/pxecmd.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/raid.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/raid5rec.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/raid6rec.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/read.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/reboot.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/reiserfs.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/scsi.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/search.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/serial.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/setjmp.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/sfs.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/sh.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/sleep.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/tar.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/terminfo.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/test.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/tga.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/true.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/udf.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/ufs1.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/ufs2.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/uhci.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/unicode.pf2
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/usb.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/usb_keyboard.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/usbms.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/usbtest.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/vbe.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/vbeinfo.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/vbetest.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/vga.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/vga_text.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/video.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/video_fb.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/videotest.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/xfs.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/xnu.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/xnu_uuid.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/zfs.mod
/media/36637a97-e88d-42b1-b560-5e6c4b9b0cc1/grub/zfsinfo.mod

95% of how-tos I read seem to be obsolete.

---

### Post by louieb on 2009-12-01
The how to I linked to is for a dedicated partition using GRUB legacy. Not exactly outdated - Ubuntu Karmic is the 1st and only distribution that at this time defaults to using GRUB2.  (those are GRUB2 files you listed).

Look in the /boot/grub folder of one of your other distributions you should find either menu.lst or grub.conf maybe both. 

Or if you want to have your dedicated GRUB partition use GRUB2 
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

Look around the site its all about multi booting with an emphasis on Ubuntu. 
> I can't find any plain how-to's. Sheesh. Who beyond one-tenth of one percent of computer users is the intended audience for these?

:DI guess that you and me.  Linux only has about 3% of the desktop market.

---

### Post by oldfred on 2009-12-01
Herman has a lot of good info on his site for both old and new grub, partitioning and multibooting. louieb gave you a link to just part of his site.

There is an older link to booting 145 systems. While it is older it shows some of the planning required to set up for multiple operating systems:

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by darkod on 2009-12-01
With the new Grub2 I see no reason for chainloading and complicating the boot process with installing other grub copies to every partition holding an OS. IMHO.
Plan your partitions carefully, that's the most important part. Like others said, no separate /boot and no common neither, not needed and it doesn't work.
At the end install Karmic last and grub2 on the MBR, it should pickup all other distros. If not, it still has mechanisms for adding custom entries.
You don't necessarily have to plan to install Karmic last, you can always reinstall Grub2 later. Or even better, for any distro installed after Karmic select advanced setting during the install and tell it not to install bootloader. That keeps your grub2 intact on the MBR. And just a simple update-grub will add the new distro in it.

---

### Post by booksnmore4you on 2009-12-06
I found best success doing basically what darkod said.  I just made a swap partition and numerous partitions for distros and installed each distro in total into it's own drive. Each one I installed so far sorts out grub and boot fine. Simple. Now I can keep my hair. :D

---

### Post by SeePU on 2009-12-17
Hey, I think this thread is great!  Interesting ideas and options suggested by you guys!  Imho, both Louie and Darko have good yet slightly different angles on it.

I have used a separate grub partition on my desktop (also called a dedicated or separate boot partition).  It seems to work fine.  I've had some issues in the past but got around them and solved it.

However, on my laptop, I have less room.  I am not too fond of extra partitions for /home and /boot.  I always use a common swap partition.  

I upgraded to a larger drive but it's still only 160GB.  I want to multi-boot, too, so around 4 or 5 distributions and 1 Windows operating system (XP).

I am not yet decided on the procedure I will use.  To do it the traditional way or use a dedicated grub partition?

Also, since Ubuntu 9.10 uses Grub 2, that is a bit of variety into the equation.  I think it's an interesting concept of installing Ubuntu 9.10 last and let the Grub 2 detect the rest of the operating systems and then boot that way.  How well does Grub 2 detect Fedora 12?   Anyone know?  I wanted to include Fedora as one of the distros.

Also, if I use a dedicated grub partition, where in the disk hierarchy are you guys putting it?  Do you place it in as one of the primary partitions or use the first logical partition you create?

This is my idea:
Partition 1 - Primary - NTFS - Windows XP - 15GB
Partition 2 - Primary - NTFS - data (who cares) - 15GB
Partition 3 - Primary - ???? - could be grub partition or just another NTFS 
Partition 4 - Extended (uses up last primary partition):
partition 5 - Logical - (could be grub partition - 100MB)
partition 6 - Logical - swap - 2GB
partition 7 - Logical - ext3 - Debian - 30GB
partition 8 - Logical - ext4 - Fedora 12 - 30GB
partition 9 - Logical - ext4 - Ubuntu 9.10 - 30GB
partition 10 - Logical - ext3 - data partition.... etc. etc.

Does this set up make sense?  I'm just trying to decide two things:
1) if I use a dedicated grub partition, do I use Grub Legacy or Grub 2 - also, where should I place it?
2) if I *don't* use a dedicated grub partition, how should I arrange the partitions and should Ubuntu 9.10 be last since it uses Grub 2?

I am sorry to keep this thread going with a bit of my own two cents into it.  I apologize to the OP if he/she wishes it back on to his specific project.  If my question is of interest to the OP or anyone else, I am then glad and can offer my limited experience and ideas if requested. :)

Excellent discussion and bound to help people eventually! :)

---

### Post by lostinxlation on 2009-12-18
You can update Grub2 anytime to let it detect other OS' so that it doesn't matter when you install Ubuntu. Having said that, it might be safer to install Ubuntu at the last to avoid potential issue with sharing swap because I had to install Ubuntu at the last when I install Slack and Xubuntu in the same HDD. I don't know how Debian and Fedora handle the swap space installation, but I know at least Ubuntu doesn't rip off the swap from the other OS' which already are present in HDD).

---

### Post by tommcd on 2009-12-18
> **lostinxlation said:**
>  Having said that, it might be safer to install Ubuntu at the last to avoid potential issue with sharing swap because I had to install Ubuntu at the last when I install Slack and Xubuntu in the same HDD. I don't know how Debian and Fedora handle the swap space installation, but I know at least Ubuntu doesn't rip off the swap from the other OS' which already are present in HDD).
I have also had problems with Ubuntu detecting the shared swap partition after installing other distros. It is all due to those dreaded UUIDs that Ubuntu, and a few other distros, like Mandriva and I think Fedora, use to identify partitions. Whenever I install another distro it also formats swap, so Ubuntu creates a new UUID for swap the next time I boot Ubuntu and the swap doesn't load.
There is an easy fix for this. First, to turn on swap:
```
sudo swapon /dev/sdXY
```
Where X is the hard drive number, and Y is that partition number of your swap. For me on my desktop it is /dev/sda3. **Be sure you use the correct partition when you run swapon**.
Then to get swap to boot automatically, first find out the new UUID of swap:
```
sudo blkid
```
This will output the UUIDs of all partitions. For my swap I get:
```
/dev/sda3: TYPE="swap" UUID="49e5e2d4-2c86-468d-8722-087f4d3cbe55" 

```
Then edit /etc/fstab and replace the UUID for swap in fstab with the new UUID you got from blkid. Note: you will omit the quotes " " that are present in the output of blkid for the UUID since fstab does not use them.
Other distros, like Slackware, that don't use UUIDs never have this problem.
Note #2: I always backup system files for safety before editing them,.

---

