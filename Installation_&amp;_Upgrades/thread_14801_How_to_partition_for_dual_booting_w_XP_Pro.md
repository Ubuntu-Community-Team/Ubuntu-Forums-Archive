---
title: "How to partition for dual booting w/ XP Pro?"
date: 2005-02-09
forum: Installation &amp; Upgrades
---

### Post by sridhar on 2005-02-09
I have like this:

[IMG]http://img226.exs.cx/img226/9941/14sx.jpg[/IMG] 

[IMG]http://img43.exs.cx/img43/138/29wz.jpg[/IMG] 

C is data partition. D has windows XP Pro.

Can you guys please check this small flash movie and tell me if what I am doing is correct or not?

[Flash movie](http://sridharkatakam.com/sri-addons/flashots/PartitionMagic/) 

If it is, should I have to create another unallocated partition for swap? If so, how many MB/GB should it be?

I want to split C drive into two parts. 10 GB for Ubuntu and the rest of it for data storage (NTFS). Can I do this using Ubuntu itself or do I have to use Partition Magic? 

Since C is a primary drive, will I be able to boot into windows if I partition it? i.e., may be it contains the boot record? 

What is the best course of action for me (ideally w/o the loss of existing 15 GB of data in C & the ability to boot into Windows xp)? 

System specs:

CPU Type: AMD Athlon 64, 1800 MHz 2800+
Motherboard Name: MSI K8MM-ILSR (MS-6741) (3 PCI, 1 AGP, 1 CNR, 2 DDR DIMM, Audio, Video, LAN, IEEE-1394)
Motherboard Chipset: VIA K8M800, AMD Hammer
System Memory: 192 MB
BIOS Type: AMI (04/21/04)

Thanks.

---

### Post by rcliii on 2005-02-09
Looks like you're on the right track.  You'll need a swap partition.  The old rule of thumb was always 2x the physical memory in your machine.  So, I'd recommend 384Megs for you.  Then you're ready to install... 

As I recall the Ubuntu installer tries to take the whole disk (assuming an installation on a new machine, or at least one where windows is not sticking around).  Make sure you pay attention to the partitioning step and force Ubuntu to use the partitions you've freed up for it.  The installer should then recognize the Windows partition and set it up as a boot option.

---

### Post by farmer on 2005-02-09
Also, make that data partiton FAT32. Linux can't write NTFS, only read. Unless, of course, you don't need to be able to write from Linux.

---

### Post by sridhar on 2005-02-10
[img]http://img135.exs.cx/img135/7751/52nt.jpg[/img]

10 GB for Ubuntu
512 MB for swap

Does that seem correct? Can I apply changes?

---

### Post by Jos Walrave on 2005-02-10
I personally always partition with DRUID.

You can keep it simple:
- /boot, approximately 100 MB, bootable flag ON, ext3
- swap partition of twice your RAM (int. mem), a little more won't harm you
- / , size of whatever you like, ext3

If I were you I just would leave all of the non NTFS partitions unallocated. With DRUID you can partition the unallocated part of your hard disk. NTFS can only be read as is already mentioned. Wouldn't bother too much with partitioning with PM, you can do all this stuff in the installation process. Use the paramaters as mentioned above. The NTFS partition will be recognized by grub. You may need to extend your fstab though.

Grtx,
Jos Walrave

---

### Post by sridhar on 2005-02-11
This might be sounding like a essay but giving all the details is needed for troubleshooting in my opinion. 

I resized C drive like so:

[IMG]http://img216.exs.cx/img216/8114/75fh.jpg[/IMG]

and let Ubuntu setup itself in the new unallocated space. The installer seemed to have created 10.3 GB Ext3 partition for / and another 300 MB for swap. 

During installation I was asked to select the graphic card driver or something like that and I didn't know what it was...just pressed 'Enter' ('vesa' was selected by default). 

Once the installation (along w/ the security updates) was complete, it said 

> To revisit setup, run base-config

and showed the $ prompt and flickered twice and showed up a screen (where it tried to launch the GUI) that said 

> I can't start X server (your graphical interface). It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem 

and when I said yes:

> This is a pre-release version of XFree86, and is not supported in any way.....

XFree86 Version 4.3.0.1 (Ubuntu 4.3.0.dfsg.1-6ubuntu25.120041117134135 root@)
Release date: 15 August 2003
X Protocal Version11, Revision 0, Release 6.6
Build O.S Linux 2.6.8.1-3-amd64-genericX86-64[ELF]
Build date: 17 Nov 2004

Module Loader Present

Upon pressing OK, 

> I will disable X server for now. Restart GDM when configured correctly.

Upon pressing OK, I am shown the $. I entered the username and password (that I setup during installation) and logged in. When I type "baseconfig", it says:

> /usr/sbin/base-config:line25: /var/log/base-config.timings:Perm denied

I tried 'startx' and was unsuccessful.

I rebooted the computer and the grub bootloader isn't showing up for long enough time for me to see if Windows XP is present as an option. It's like I start the PC and immediately Ubuntu loads up. I rebooted again and pressed Esc or some other key and found that this time to my horror, Windows isn't present.

How do I get out of this mess? 

How do I get the graphical interface running in Ubuntu?

How do I get the dual boot option?

If nothing, how can I undo all I did and go back to Windows XP?

:(

---

