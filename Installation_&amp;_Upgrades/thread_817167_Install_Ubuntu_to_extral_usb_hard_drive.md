---
title: "Install Ubuntu to extral usb hard drive"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by Dave2k6 on 2008-06-03
Hi

I wish to install Ubuntu/Kubuntu 8.04 to my laptop's USB hard drive.

I have already got the hard drive partitioned as:

300Gb NTFS - Used as a storage drive for music, videos, downloads, etc.
Aprrox. 167Gb Unallocated - Ready for Ubuntu/Kubuntu (165Gb root and 2Gb swap).

The USB hard drive is always connected to laptop, even when I go to my friends or family, I always make sure USB drive is connected and powered up before powering up laptop.

Can I just install Ubuntu/Kubuntu 8.04 to the USB drive with GRUB on same partition (as I'll use Vista's Boot Manager), or do I need to edit anything after installation ?

---

### Post by Dave2k6 on 2008-06-03
I have now installed Kubuntu onto the USB harddisc, which went without a hitch, once I got round the initramfs/BusyBox issue that I got when booting the Kubuntu Live CD.

The work round was press F6 and added irqpoll to end of boot string, then it booted into Kubuntu.

The only issue I have now is that EasyBCD doesn't not (as of v1.7.2) see any partition on removable devices, so I'm not able to add a boot entry to Vista's boot manager to boot in Kubuntu (as I installed GRUB to Kubuntu's own partition, as I wished to use Vista's boot manager instead).

Can I use SuperGRUB to boot into Kubuntu to allow me to finish setting up Kubuntu (edit Kubuntu's menu.lst file to include irqpoll), whilst I wait for EasyBCD to support seeing partitions on removable USB harddrives.

---

### Post by logos34 on 2008-06-03
> **Dave2k6 said:**
> Can I use SuperGRUB to boot into Kubuntu to allow me to finish setting up Kubuntu (edit Kubuntu's menu.lst file to include irqpoll), whilst I wait for EasyBCD to support seeing partitions on removable USB harddrives.

Either that or SGD on a USB flash drive

---

### Post by Dave2k6 on 2008-06-04
OK. I have also now tried the SuperGRUB cd, and that only sees my laptop's internal drive.

Looks like the USB drive can't be seen by the laptop at boot up. In BIOS, I have also tried the removable media boot option, but that the same as setting it to boot from cd/dvd drive.

What I need to do is create a /boot partition on my internal harddrive that allows me to boot into GRUB from Vista's Boot Manger, then after loading the USB modules, continue booting the rest of Kubuntu from the usb hard disc.

Any suggestions on how I go about this ?

---

### Post by logos34 on 2008-06-04
> **Dave2k6 said:**
> Looks like the USB drive can't be seen by the laptop at boot up. In BIOS, I have also tried the removable media boot option, but that the same as setting it to boot from cd/dvd drive.

That's actually the first thing you should have checked--whether the Bios supports USB boot.  

'removable media'=floppy

See this:
[http://www.supergrubdisk.org/wiki/GrubOnRemovableExternalHardDiskNotBooting](http://www.supergrubdisk.org/wiki/GrubOnRemovableExternalHardDiskNotBooting)

> What I need to do is create a /boot partition on my internal harddrive that allows me to boot into GRUB from Vista's Boot Manger, then after loading the USB modules, continue booting the rest of Kubuntu from the usb hard disc.

Any suggestions on how I go about this ?

That approach is probably your best bet.

Here you go:
[https://help.ubuntu.com/community/BootFromUSB#head-c56d6ffb96b299d571031b05360d2a43e5769d67](https://help.ubuntu.com/community/BootFromUSB#head-c56d6ffb96b299d571031b05360d2a43e5769d67)

---

### Post by cyclonedr on 2008-06-04
I installed to an external hard drive by first booting the live Cd, clicking install.  Then I set up the partitions in the partitioner.  Make sure the partitions are unmounted before installing though, as I have had issues and have heard that others have had issues with that as well.  You can do that by right clicking on the icons on the desktop and selecting Unmount Volume.  When you get to the last page click on advanced and then set the path to /dev/sdb or whatever linux sees your external drive as. You can fdisk -l from the terminal to find out what it's called.  Then install.  Were not done yet.  When your computer starts up, press F12 or whatever button you use to get a boot menu and select your USB drive.  When the GRUB menu comes up select the first entry and press e, then set hd1,2 to hd0,2, remember only change the first value.  Now press enter and you should be able to boot to Ubuntu without affecting your windows install

---

### Post by logos34 on 2008-06-04
> **cyclonedr said:**
> Were not done yet.  When your computer starts up, press F12 or whatever button you use to get a boot menu and select your USB drive.  When the GRUB menu comes up select the first entry and press e, then set hd1,2 to hd0,2, remember only change the first value.  Now press enter and you should be able to boot to Ubuntu without affecting your windows install

You misunderstand the problem: his Bios apparently does not support USB boot/can't see the external drive at startup.  Which is why EasyBCD can't either.

---

### Post by cyclonedr on 2008-06-04
Oops, sorry, I guess I read the post a little to fast.  Thanks for "waking me up"

---

### Post by Dave2k6 on 2008-06-04
lol. I sometimes 'speed read' posts too, but try not to.

Anyway, will give the create boot partition on internal hard drive a go, and see where it gets me. At least this way, I can use EasyBCD, so I can boot linux from Vista's Boot Manager.

Also, an added bonus is, that if the USB drive isn't plugged in, I can still boot to Vista.

Wish me luck :D

> 'removable media'=floppy

lol. Strange that, as this laptop doesn't have a floppy drive in it. So, that BIOS boot option was 'useless' lol.

---

### Post by logos34 on 2008-06-04
> **Dave2k6 said:**
> Strange that, as this laptop doesn't have a floppy drive in it. So, that BIOS boot option was 'useless' lol.

but the board may have a floppy connector.

---

### Post by Dave2k6 on 2008-06-04
Back again.

The installer can't format the 500Mb partition I have at the end of my laptop's internal drive. Keeps saying failed (tried ext2, ext3, and fat32 (fat32 not allowed for /boot says installer)).

Any ideas ? Can I use gparted to format the /boot partition to ext3 before I use the installer to install the system ? Or do I quit whilst I'm ahead lol

---

### Post by logos34 on 2008-06-04
> **Dave2k6 said:**
> Can I use gparted to format the /boot partition to ext3 before I use the installer to install the system ? Or do I quit whilst I'm ahead lol

Sorry to keep you waiting.

Um, yes, use gparted to format it ext3, then try the installer again.

If it still doesn't work, then maybe there's problem with the placement at the very end of the hard disk. But I hope that's not the case, because that would mean you'd have to put it at the head of the disk, which could possibly cause boot problems with vista.  But I'm getting ahead of myself

---

### Post by Dave2k6 on 2008-06-04
Yay! The GParted Live CD managed to format sba2 partition as ext3.

I also reformatted the sdb2 (root) and sdb3 (swap) partitions as ext3 and linux-swap respectively.

One thing I noticed is that sda1 is flagged as 'boot', which is correct as it's where Vista (and it's Boot Manager) live.

My question is this... what happens to this boot flag when i mount sda2 as /boot and install GRUB to sda2 (I assume it should stay flagged as boot) ?

---

### Post by logos34 on 2008-06-04
another thing just accured to me: did you shrink vista (by 500 MB) using it's own disk utility or the installer?  You need to use vista. otherwise that can cause problems

---

### Post by Dave2k6 on 2008-06-04
I'm ahead of you on that one lol

I used Vista's own disk manager. Wasn't going to let GParted screw up my Vista installation! lol

---

### Post by logos34 on 2008-06-04
> **Dave2k6 said:**
> Yay! The GParted Live CD managed to format sba2 partition as ext3.

I also reformatted the sdb2 (root) and sdb3 (swap) partitions as ext3 and linux-swap respectively.

One thing I noticed is that sda1 is flagged as 'boot', which is correct as it's where Vista (and it's Boot Manager) live.

My question is this... what happens to this boot flag when i mount sda2 as /boot and install GRUB to sda2 (I assume it should stay flagged as boot) ?

ok, good.  I was beginning to wonder if vista was going to cause a problem because the general rule is to always use vista to resize itself.  You can safely **format** it with gparted, though.

Just leave the boot flag on sda1.  Windows is the only os that cares about it.  (And sometimes not even that--back when I was dual-booting windows booted fine no matter whether flagged or not)

---

### Post by logos34 on 2008-06-04
> **Dave2k6 said:**
> I'm ahead of you on that one lol

I used Vista's own disk manager. Wasn't going to let GParted screw up my Vista installation! lol

cool

---

### Post by Dave2k6 on 2008-06-04
OK. So I can now go ahead and install Kubuntu 8.04 ?

The reason I was worried about the 'boot' flag is because when you install linux, GRUB sets the flag on which ever partition it is installed to (hence my old sdb2 was flagged as 'boot').

---

### Post by Dave2k6 on 2008-06-04
OK. Tried to install Kubuntu again and it failed.

Something along the lines of can't write to /boot partition.

I then exit the installer, load konsole and typed 'sudo fdisk -l' and it onlys lists my sdb (external) drive, yet before install it showed both drives.

From google searching, it seems the SATA controller is causing the problem.

Any ideas ?

---

### Post by logos34 on 2008-06-04
not sure why it's choking on that ext3 /boot.

I'd try installing again, but this time tell it to write grub to the bootsector of linux root.  (i.e. 'Ready to install' step>Advanced button>change '(hd0)' to **/dev/sdb2**). Then manually copy kernels & all over to separate /boot (sda2) using the howto I gave you.

---

### Post by Dave2k6 on 2008-06-04
The error I get is 'The installer needs to remove operating system files from install target, but was unable to do so. The install cannot continue'.

That's when I set sda2 as /boot don't format (as formatted by GPartEd), then GRB install to /dev/sda2.

I exitted the installer, and typed 'fdisk -l' in terminal and again sda has disappeared, and typing 'dmesg' shows I/O error messages for sda.

---

### Post by Dave2k6 on 2008-06-05
I'm happy to report that I now have Kubuntu installed, after 6 hours (11pm til 5am!!!)

What fix it was booting the live CD with this at the end of the boot line after --

all_generic_ide floppy=off irqpoll

Which worked and allowed me to format sda2 as /boot (ext3), sdb2 as / (ext3), and sdb3 as swap.

I don't think the floppy=off was needed, but left it in as my laptop has no floppy drive, but the motherboard does have a FDC (weird??).

All that's left to do now is use EasyBCD to add Kubuntu to Vista's Boot Manager, and then test to see if I can actually get into Kubuntu (I know to readd the extra boot parameters at the GRUB menu). Once in Kubuntu, I'll edit menu.lst to permanently add those extra boot parameters.

---

### Post by logos34 on 2008-06-05
Nice work.  Probably would have taken me a week to figure out the necessary boot option!

Post back as soon as you are successful (or not) with usb boot.

In the meantime I have to deal with my own problems--the most serious being my router keeps cutting out on me.  I'm having to reset it to factory defaults constantly.  Refuses to accept password and any setting other than dynamic IP (whereas my service is actually PPPoE DSL.  Did it change without my knowing?)

So many mysteries...

---

### Post by Dave2k6 on 2008-06-05
It booted successfully to Kubuntu.

Also, no need for me to edit menu.lst to add the extra boot parameters, as they were automatically added when the system was installed.

All 76 updates installed fine, including the new kernel (2.6.24-18).

One question: in Ubuntu I used firestarter to config the iptables to what I need. What is Kubuntu's firewall config called ?

---

### Post by logos34 on 2008-06-05
> **Dave2k6 said:**
> It booted successfully to Kubuntu.

Super!

> One question: in Ubuntu I used firestarter to config the iptables to what I need. What is Kubuntu's firewall config called ?

Guarddog?

---

### Post by Dave2k6 on 2008-06-05
> **logos34 said:**
> Guarddog?

Hi

Tried guarddog and it blocked me from accessing the net, and I was at lost on how to configure everything. So, I have installer fire starter for now, as it's one I have on my Ubuntu install and know how to use it.

By the way, I have an external USB digital tv box (AverMedia USB DVB-T) that I can connect to my laptop to view freeview. Will kaffine allow me to watch tv with it, or do I need to download something else ?

---

### Post by logos34 on 2008-06-05
> **Dave2k6 said:**
> By the way, I have an external USB digital tv box (AverMedia USB DVB-T) that I can connect to my laptop to view freeview. Will kaffine allow me to watch tv with it, or do I need to download something else ?

dunno.  someone else may know the answer

---

### Post by augusto.sisa on 2008-06-05
I have a similar problem. I installed Ubuntu in a new External USB Drive, and install grub in the MBR of the external drive. At this time I can start WinXP from internal HD and Ubuntu from external HD controlling if I connect the external HD or no during boot time.  The  problem is that I can see any partitions in the External HD from WinXP so I can use a FAT partition that I want to use for share files between these OS and with other computers. 

So I you can help me with your experience I will glad you.

Augusto

---

