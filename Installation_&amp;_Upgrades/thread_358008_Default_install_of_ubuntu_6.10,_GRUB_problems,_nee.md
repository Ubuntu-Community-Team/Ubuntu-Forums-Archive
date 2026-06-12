---
title: "Default install of ubuntu 6.10, GRUB problems, need to restore/recreate MBR"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by MattyUSA on 2007-02-10
Hi

In short: A default install of ubuntu 6.10 from the live CD replaced the MBR of my C: drive and installed the GRUB bootloader. How can I move this bootloader to another drive and restore my original MBR to the C drive?

The full description of what I did, what I have and what I need follows:

I am new to ubuntu and fear I got myself into trouble with GRUB and my particular setup. I could really use some help in sorting it out. whilst the systems work and are stable now it is not the configuration I desired and a wrong move now in attempting to restore the MBR could mean disaster for me.

I'm hoping someone will take pity and help me out.

I have read other related forum posts but couldn't find one similar enough to my setup for me to be comfortable following its advice.

I am computer literate and comfortable with command line but I am new to Linux (beyond a shell account on my server) and very new to ubuntu.

I wanted to trial a flavor of Linux alongside windows for a period of time before I considered jumping the MS ship.

Here is my hard drive setup.

2 IDE drives internal to the PC
    -> 1 is 80gb, single partition, NTFS, contains Windows XP Pro, was the C: drive
    -> 1 is 80gb, single partition, FAT32, contains data, was the D: drive

1 external USB hard drive
    -> Ubuntu controller actually recognizes as SCSI4 it is 30gb and has the partitions typical with the full install of ubuntu (ex2fs? etc)

I wanted to install ubuntu onto the external drive an boot off that whenever I felt like getting to learn ubuntu. When the drive was unplugged windows should load as normal uninterrupted. I was happy and prepared to change BIOS boot options to switch between the two.

I also thought I could take the external hard drive with ubuntu to other PCs and boot ubuntu off their systems should the need arise (assuming suitable BIOS).

I partitioned the USB drive happily letting ubuntu take the entire disk. I saw that it was recognized as sdb. Then the installer got to the screen that said BRUG will be installed to (hd0).

Concerned that the BMR for my windows disk was going to be wiped I tried continuing with (sbd). The installation failed with an error. So I repeated with (sdb0) and (SCSI). Failing again.

On the forth attempt I opened a terminal and entered grub I then used the geometry and tab completion to see the structure of hd0. to my surprise it showed the Linux structure, the Linux swap partition and so on. 

grub> geometry (hd0)
drive 0x80: C/H/S = 3649/255/63, The number of sectors = 58633344, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

Ahh ha I thought for whatever reason the install thinks the USB drive IS hd0. So I left the default option for GRUB to be installed to as hd0.

opps.

Now I have installed GRUB on the MBR of the primary IDE hard drive (C:) containing Windows Pro. Not at all what I wanted.

After using it a few times I can get an error 21 whilst trying to load the GRUB screen if the USB drive is not connected to the system. If I try to BIOS boot to the USB hard drive I get a failure saying can''t load operating system (I guess thanks to the unsuitable MBR on the USB hard drive).

Anyway here is what I need to do and need some help accomplishing.

1> I want to restore the MBR on the primary IDE drive containing windows so that it loads windows uninterrupted when the BIOS is set to boot from that hard drive. I don't want the GRUB boot loader asking me what OS to use when that drive is booted too.

2> I want to install a suitable MBR on the USB hard drive containing ubuntu so that it CAN be booted too when the BIOS is set to boot to the USB hard drive. I don't mind GRUB asking me which ubuntu version I want to load at that point.

I currently have ubuntu booted and am happy using partition manger, or following terminal commands.

I have the XP install disk and I presume could boot into recovery console off that disk if I knew the commands to then use to restore the MBR.

PS: my vote is that this screen of the installer needs to be made more newbie friendly. I had no idea what GRUB was at first, then how to find the correct string to indicate the device/partition with the ubuntu install. Forum posts led me to the grub console command and my incorrect conclusion as to what I saw.

Many thanks in advance.

MattyUSA

---

### Post by confused57 on 2007-02-10
Here's how to restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The Super Grub Disk is also capable of restoring the mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I've never installed to an external USB hard drive, maybe this will help you:
[http://www.ubuntuforums.org/showthread.php?t=226638&highlight=success+external](http://www.ubuntuforums.org/showthread.php?t=226638&highlight=success+external)
[http://ubuntuforums.org/showthread.php?t=308027&highlight=install+external+hard+drive](http://ubuntuforums.org/showthread.php?t=308027&highlight=install+external+hard+drive)


There is always the possiblity you could add an entry to your Windows mbr, after you get it restored, to boot your USB drive with Ubuntu.

---

### Post by MattyUSA on 2007-02-10
THANK YOU confused57

You are a godsend. Those links look like they'll help me to get things working they way I need them. At the very least it gives me windows back which is important for work.

> There is always the possiblity you could add an entry to your Windows mbr, after you get it restored, to boot your USB drive with Ubuntu.
That involves the boot.ini? What sort of text line would I need?

I haven't read all the links you posted yet, the answer may be there. Thanks again.

Regards,
MattyUSA

---

### Post by salvo on 2007-02-10
> **MattyUSA said:**
> 
Ahh ha I thought for whatever reason the install thinks the USB drive IS hd0. So I left the default option for GRUB to be installed to as hd0.

opps.

Now I have installed GRUB on the MBR of the primary IDE hard drive (C:) containing Windows Pro. Not at all what I wanted.



I use BootIt NG to manage my partitions.  During 6.10 installation, instead of hd0 I pointed GRUB to hd0,0 which was the partition that I installed / to.  This prevented GRUB from clobbering my MBR.

---

### Post by MattyUSA on 2007-02-10
Thanks Salvo

At the time I didn't know you could include , and numbers to specify different partitions. In hindsight I could have unplugged or disabled from BIOS the internal hard drives. The link previously posted: [http://ubuntuforums.org/showthread.php?t=308027&highlight=install+external+hard+drive](http://ubuntuforums.org/showthread.php?t=308027&highlight=install+external+hard+drive)
was really very good for me. After I have finished backing up and restored the windows default MBR, I shall follow its instructions to the letter

If anything my experience and your comment probably point to the fact that this screen of the installer needs to be made more newbie friendly. Well thats how my vote would go. Ubuntu was suggested to me on the fact that its desktop environment was easier to learn and less complicated than others. So far I have to say I'm very impressed, except for this one hiccup which could have been a disaster for me. Had confused57 not posted the link to the article I would have walked away from ubuntu and found another distro to trial and been FAR more cautious the second time around.

cheers,

Matt

---

### Post by salvo on 2007-02-11
> **MattyUSA said:**
> 
If anything my experience and your comment probably point to the fact that this screen of the installer needs to be made more newbie friendly.

I agree, MattyUSA.  I got lucky and stumbled into critical advice from the BING [_documentation_]("http://www.terabyteunlimited.com/kb/article.php?id=171").

---

