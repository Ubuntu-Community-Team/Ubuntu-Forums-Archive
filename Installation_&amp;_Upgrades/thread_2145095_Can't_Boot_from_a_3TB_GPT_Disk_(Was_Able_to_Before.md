---
title: "Can't Boot from a 3TB GPT Disk (Was Able to Before)"
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by svet-am on 2013-05-14
I don't know if this is really an Ubuntu problem but thought I'd post here as a first go at solving this....

My mainboard is an Intel DX48BT2. I have it configured to treat SATA drives as AHCI and I have UEFI boot enabled in the BIOS.

My SATA drives are:
SATA0 : Seagate ST3000DM001 (3TB)
SATA1 : Sony DVD-RW
SATA2 : Pioneer Blu-Ray

I am booting Ubuntu 13.04 x86_64 from a USB stick. I can boot the USB stick just fine. Initially I went into the installer and I specified my partition layout like this:

1MB : GPT Reserved Area
128MB (ext2) : /boot
~2.99TB (ext4) : /
8198MB : swap

I am also telling the installer to install the bootloader into the MBR (using the option in the installer GUI)

When I try to boot, the computer fails to boot claiming "no bootable device found".  I re-booted into my USB stick and (thinking something was wrong with my partitioning), I used gparted to re-initialize the drive as a GPT drive with no paritions defined.  I then went through the Ubuntu installer and let it select its own default scheme.  This yielded the same problem - "no bootable device found"

I pulled out my 3TB drive and put in a 1.5TB drive and it works just fine.  I pulled that out and put in an older 3TB drive that I've used before and it worked just fine.

I re-installed my new 3TB drive and checked the partitions and I see them all there. I can mount and browse them and I see the files I expect.  I rebooted into my USB stick and installed "boot-repair" and ran it.  I did the default repair and it says that it was successful but upon reboot, I get the same error -- "no bootable device found."

I used gparted again to clean the drive, but this time I configured it as a standard MBR-type disk (I was okay with losing the extra space for the sake of this test) and then installed Ubuntu using the default partition scheme.  It still won't boot.

It seems to me (I may be wrong) that the partitions are okay but it's the MBR that is messed up in that the BIOS cannot find where to boot from.  Is this correct?

I did some Googling and came across these references:
[http://forums.gentoo.org/viewtopic-t-716015.html](http://forums.gentoo.org/viewtopic-t-716015.html)
[http://blog.fpmurphy.com/2010/01/uefi-booting-fedora-12-on-an-intel-dx48bt2.html?output=pdf](http://blog.fpmurphy.com/2010/01/uefi-booting-fedora-12-on-an-intel-dx48bt2.html?output=pdf)

I've read through them and neither really seems to apply to my situation.

A friend suggested doing a Windows install just for the sake of getting the MBR set up and then go back and install Linux as a GPT drive.  I don't know if this holds any merit as I believe that re-configuring the drive as GPT would wipe out the MBR anyway.... (again, I may be wrong).

Does anyone have any advice as to what I can try?

---

### Post by TheFu on 2013-05-14
I do not have an answer, but .... perhaps a little different disk layout would be helpful?  I've never attempted to boot off a GPT disk and don't have any UEFI systems.  I'm afraid. ;)  Thanks for testing this. I have started using GPT for all HDDs over 300G - I love having 100+ primary partitions and having the partition table written at opposite ends of the HDD.

Here's what I would do:
* GPT format
* /boot - 500MB - a little more room will be nice when a few kernels are loaded. Bad things happen when /boot runs out of room during an update.
* / - 20G for OS and apps - more is overkill, IMHO.
* swap - 2G or less.
* /home - 5-20G for small files, docs and settings; size depends on the number of users and how much you can easily backup. It is nice to be able to wipe the OS yet leave /home alone.
* /data - the rest for large files like music and media; 

I don't **know** that having / with a huge file system is an issue, but it could be.

BootInfo [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) will provide data and facts to help determine the real issue on your system.

Good luck!

---

### Post by oldfred on 2013-05-14
+1 on theFu suggestions.

But do you want UEFI or BIOS/CSM boot?
Ubuntu will boot with either UEFI or BIOS from gpt partitioned drives. There used to be a bug on very large / (root) partitions, but they claim they fixed it. But we still see some BIOS systems (usually USB) with very large / that will only boot from the first 100GB. Or /boot or the entire smaller / partition must be fully inside the first 100GB. The rest of the drive can be /home or data.

If you may ever want to boot with UEFI then include a 200 to 300 efi partition as the first partition even if you do not want or need it now with BIOS booting. And the 1MB partition must be unformatted and have the bios_grub flag set for grub to install correctly with gpt partitioning and BIOS boot.

How you boot install flash drive is how it installs. Or if you boot installer in UEFI from UEFI menu it installs in UEFI mode. You have booted in UEFI mode if you get grub menu.
If from UEFI menu you boot in CSM/Legacy/BIOS mode then it will install in BIOS mode. But default install still is just / & swap and on monster drives root is just too large. You know you booted install in BIOS mode as it uses syslinux boot loader and you get the tiny keyboard & person accessiblity icons at bottom of screen for a few seconds.

What video card? Often nomodeset required. If you have only one system installed you never get grub menu and it just goes to booting. But you get black screen unless you have nomodeset in grub linux line for nVidia and many other video systems. Hold shift key from BIOS, with UEFI sometimes shift key works others say escape works to get the grub menu. Then use e and replace quiet splash with nomodeset.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

