---
title: "[SOLVED] initial Intrepid boot fails, drop to &amp;quot;initramfs&amp;quot; Sata and IDE drives absent"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by amgalitz on 2008-11-02
Hello, firstly thanks to all the efforts of the many people who have brought ubuntu this far and help on the many forums.

I am having a wretched time getting Intrepid (and Hardy) to initially boot after the liveCD install. The problem appears to be related to recognition of the IDE and Sata Drives. I've successfully installed ubuntu 8.04 and 8.10 on my desktop Opteron(64b)/Asus A8N-e, and a very old BX6 MB with a 400Mhz Celeron as a file server. The A8N-e has a mix of IDE and Sata drives and I multiboot Windows XP, Ubuntu 8.04 and 8.10 on it, with a separate GRUB partition, with the two Ubuntu's sharing a single /home partition. The celeron is a multiboot of the original Gentoo (got tired of compiling and blocking dependencies) and the current ubuntu 8.04 server edition. While this has taught me much, I am still very much a beginner with linux.

I tried to research hardware but missed that there seem to be issues with the AMD 770/SB700 chipset and the current kernel. This maybe related to my running 4gb of Ram. I saw many ubuntu/linux people using the Asus M3A78 so thought it would be ok.

HARDWARE. ASUS M3A78 (bios 703=latest), AMD 4850e (64b Dual Core), 2 x 2GB OCZ memory (memtested off install cd for 40 hours with no errors), WD IDE 120 GB, WD 1 TB SataII, LG GBC-H20Li cd/dvd/bd

SOFTWARE: multiple installations using 8.10 AMD and i386 desktop and alternate CDs. also tried the same 8.04 
desktop image used on my opteron system; none successful to boot. All will run as LiveCD session, even though they throw the IOMMU error.

PROBLEM. Initial boot after install throws this error:
_____________________
[INDENT][FONT="Fixedsys"]Boot from (hd0,0) ext3  *** *[FONT="Arial"];*** = UUID for partition omitted, ag[/FONT]*
Starting up ...
[   0.004000] Aperture pointing to e820 RAM. Ignoring.
[   0.004000] Your BIOS doesn't leave a aperture memory hole
[   0.004000] Please enable the IOMMU option in the BIOS setup
[   0.004000] This costs you 64 MB of RAM
Loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/*** does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/FONT][/INDENT]
--------------
output of 'cat /proc/cmdline':
 **root=UUID=*** ro quiet splash ;note** *** is the above UUID

My BIOS has no IOMMU option, see below for kernel option related.
Since the system at this point is not up, I could not find any log files to report.
The basic BIOS boot phase seem very long in the early HDD recognition phase.
Oddly the BIOS reports a Floppy present, even though there is none, and I have disabled Floppy from boot sequence.
There is a long pause with "Grub Loading Stage 1.5" visible, then "Grub loading, please wait", another long pause then the Ubuntu initial small splash screen, followed by the error above.

I can use the liveCD to run a perfectly normal instance of ubuntu 8.10. I can mount my IDE and Sata drives just fine. I can edit the installation files. I've check the fstab and it looks good.

Solutions attempts:
- multiple reinstallation with only the IDE or SATA in system,
- changed order of Sata lG optical between the Sata1 and Sata2 connectors.
- Googled on my MB, initramfs, drive not found.

- Have found several suggestions about various kernel options: iommu=noaperture pci=nomsi, all_generic_ide floppy=off irqpoll.
These seem to get system further along, but no joy. The error messages report "slow SATA link' or similar and last message is "Target doesn't have /sbin/init" with the kernel parameters above.

- Have found suggestions about changing SATA BIOS from SATA to eith AHCI or RAID. Tried both, wo success.
- Tried GRUB command editing of root location which give a file not found type error,
- Checked MD5 checksums of the iso's.
- Checked the CD's integrity with the install menu option.
- Verified my IDE HDD is in the master cable position and the jumpers are correct.

I have spent most of the weekend on this and would greatly appreciate any help. Someone out there has got to have a board like this with 4GB of RAM, a 64b processor on it, with a IDE and SATA. I don't think it is the 64b version however, as the 32 bit version still choked.

I did not include lspci output as i was not sure how relevant that is since the issue is so early in boot phase, but will be happy to boot up live session to get it.  

Steps I haven't tried:
- pulling one memory stick and running with 2GB,
- pulling the SATA optical drive and using an IDE CDROM on the IDE Slave position,
but I thought I'd ask my first ever question on a forum in all my years of 'nixing. TIA

cheers all.

---

### Post by billrad1 on 2008-11-02
I have the same problem, different hardware.
I can boot the earlier kernel from grub, and everything works just fine.

I have tried a few things. I have an older board with two megs of ram, and an Athlon 3200 processor. I have tried editing boot parameters in grub, to no avail. I am no linux expert, but I have weathered many ubuntu hazards...I guess this is one more.

The only thing peculiar about my system, is the hard drive arrangement. I have windows XP on an IDE drive, and ubuntu on an SATA drive, connected to an SATA card in a pci slot. It seems my SOYO Dragon motherboard wouldn't work with sata and ide connected to the board directly. Possibly this is an issue now.

I am almost convinced the issue is in the kernel, and certain modules either not loading, or not installed. But who knows.

---

### Post by KKop on 2008-11-02
Same type of error here.

I had been running 8.04 without any problems (after spending some time getting wireless to work).  I upgraded to 8.10, and noticed that the boot would stall (Ubunutu Bar would not move).  By pressing ESC I could eventually get to the login, but nothing would work, not even the mouse or keyboard.  The problem seems to be with assigning IRQ's to IO hardware (drives, keyboard, mouse, etc)

I get the same BIOS message at the beginning (never got that with 8.04) 

I must say I am very disappointed with 8.10.  It has been the buggiest Ubuntu so far.  I tried a clean install (not upgrading from 8.04) and it resulted in the same problems.

Hardware: HP pavilion DV9700 laptop with AMD64 and 4GB RAM

---

### Post by OriginalGrumpyOldMan on 2008-11-02
One more for the count, I was going to start a new thread when I saw this.

The new filesystem is nothing but trouble (I don't know if it's fuse specifically or related). First I wasted HOURS trying to figure out why the boot loader always got stuck as soon as I made a selection, even though it worked the first time around. Defective CD? Turned on ONE of the SATA drives.. no dice. BIOS changes... Nope.

Turns out that my add-on SATA controller MUST HAVE all 4 drives active for Intrepid Ibex to load... WTF. And then it will list those first, and my BOOT IDE drives last... unacceptable to me. sda has always been the root/boot linux drive, which is why I turned the add-on drives off in the first place (as I do occasionally anyway to save power/heat). Without ALL drives active and connected to the ADD-ON SATA controller, I.I. will simply hang, NOT seeing the  bog-standard, run-of-the-mill, motherboard-built-in IDE controller and the attached devices LIKE THE DVD DRIVE I.I. WAS BOOTED FROM (!)

I can't use a flash drive install because my mobo does not support that, so in the end I PHYSICALLY REMOVED THE CONTROLLER CARD to install I.I...

The install was successful, I booted, logged in, re-installed the controller and back to square one: I.I. now refuses to boot from the IDE drive, as described above. At least it's consistent.

Meanwhile back to Feisty, no problems here, drives off or on (and neither did the Gutsy Install CD). Maybe upgrade in another year or so?

(And on my eeePC more trouble, didn't think I would miss being able to edit fstab to fix a simple mount problem, where is the fuse equivalent?)

---

### Post by amgalitz on 2008-11-02
Thanks for replies, at least I'm not alone <G>.

I'm thinking also it is a kernel module issue since the LiveCD kernel works. I'm going to try and pull the kernel from the liveCD and manually install it, and see what happens.

It seems strange that the two of you are having a similar issue since I doubt your Southbridge chips are the same as my MB. It is actually concerning if they are very different.

here is my lspci output from a liveCD session (I'm using it to write this in a firefox session):
[FONT="Fixedsys"]
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)[/FONT]

My Main work machine uses an nVidia NForce4 Ultra chipset, and the old BX6 is an Intel 440BX. No issues.

I'm thinking of sending the M3A78 back and getting a M3N78 with a NVidia chipset rather than the ATI/AMD. Any thoughts about this? I will be googling to see if this error is associated with NVidia bases MBs. I have a 30 day return with Newegg. I like this board layout better though.

It might help to know what chipsets others are having problems with.

Good thing that the old BX6 keep chugging along; up 2 weeks with the new Hardy (record is 321 days on Gentoo, took down for maintenance)

TIA and Cheers.

ag

---

### Post by amgalitz on 2008-11-02
Interesting that you could boot when all the SATA spots were filled. I noticed that the system seemed to error on the empty SATA ports as if it were treating missing sata drives as an error condition! I also noted that with a USB drive in place it got assigned a position BEFORE the internal SATA drive, thus shifting the internal sata from sda to sdb. This is scary. I also see as you do that the Sata drive appeared ahead of the IDE. This makes no sense and is opposite of the behavior I believe on my A8N-E (at least for 8.04).

I understand the UUID concept and am working on getting used to it, but damn it is a pain when you are managing multi-boot machines and using image backup.

I gues my new box is something for the cat to lie on for a while. TG I don't need it urgently, but this is quite dissappointng after I was having such a nice ubuntu experience with  my first two machines. I'm goind to wait on converting my wife's machine over for now.

---

### Post by amgalitz on 2008-11-02
Ok, I've got to go to dinner with wife, but I did a quick mount of the installed system to compare to the liveCD session. The kernel looks the same as installed, but the 

Installed initrd.img has the installed date
[FONT="Fixedsys"]-rw-r--r-- 1 root root 8.3M 2008-11-02 19:17 initrd.img-2.6.27-7-generic
[/FONT]
the LiveCD session initrd is symlinked
[FONT="Fixedsys"]ubuntu@ubuntu:~$ sudo ls -lh /
total 6.0K
...
lrwxrwxrwx   1 root root   32 2008-10-29 21:19 initrd.img -> boot/initrd.img-2.6.27-7-generic[/FONT]

but it is not visible in /boot:
[FONT="Fixedsys"]ubuntu@ubuntu:~$ sudo ls -lh /boot
total 2.0M
-rw-r--r-- 1 root root 492K 2008-10-24 07:55 abi-2.6.27-7-generic
-rw-r--r-- 1 root root  84K 2008-10-24 07:55 config-2.6.27-7-generic
-rw-r--r-- 1 root root 122K 2008-09-11 20:11 memtest86+.bin
-rw-r--r-- 1 root root 1.3M 2008-10-24 07:55 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root 1.2K 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generi[/FONT]c

I can't find the Live session actual initrd.img, (probably hidden) and I have to look up the command line to show hidden files, but I will be divorced if I don't leave now! I will try copying it to the installed system and report. If an actual Ubuntu expert reads this and knows this is foolish, I'm all ears.

cheers.

---

### Post by amgalitz on 2008-11-03
Hmm. I can't find the liveCD session initrd.img to copy into the installed system for test. If this is possible, would someone clue me in please?

If there is a good thread on how to trouble shoot initramfs issues beyond what I and the others with similar issues have tried, could someone point me there? However, the boot sequence messages suggest this is an issue with the system hanging on the empty SATA ports. Any help from someone with a working system running off an Asus M3A78 board would be appreciated. 

I like how Intrepid is working on the machine as a running from the liveCD; I can mount the partitions from all the drives just fine. But,as above, I can't get the boot process past initramfs stage. Is this a debian/linux bug that should be reported? I've seen some issues like this reported months ago, so I'd be surprized if this is not a known issue. I don't wish to waste peoples time if this is a simple configuration issue I just have not figured out. 

Maybe I'll have to try a straight debian install and see what happens. Bummer, so close...

thanks

---

### Post by shozzbott on 2008-11-03
I have a very similar problem, with the system dropping to the initramfs directory, but the errors I see all have to do with the root disk being an unknown file type. I was running 8.04 without issue, tried upgrading, but then opted to do a fresh install of 8.1.

---

### Post by MKlemm on 2008-11-03
If you look at [this Thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=968968") you can see that I'm having the same issue...

Drivers seem to load OK, but on all available SATA channels it says "SATA link down"

---

### Post by amgalitz on 2008-11-03
I think this is a similar problem because the drive is not recognized, so of course the file type is unknown.

---

### Post by amgalitz on 2008-11-03
Yes, the SATA links being down is a message I see also. Thanks for pointing out "dmesg", I missed that it was available at the initramfs prompt. I'll check output when I get home tonight. I'm new at this type of trouble shooting. shozzbott above is having similar issue with INTEL chipset, not good. This may be worth a bug report, but I've never done one so wish to investigate this further. I still may just search for an AMD2/AM2+ board that someone has got working and exchange. I have real work to do!

---

### Post by psusi on 2008-11-03
amgaliz: can you give me a better idea of your disk configuration?  From the livecd, post the output of sudo fdisk -l and describe what each partition is there for.  Specifically which is supposed to be your root partition.  Also post the output of blkid.  Also post your /boot/menu.lst ( which is under /target/ on the livecd before you reboot after installing ).

---

### Post by cnarwc1 on 2008-11-03
I'm a nubie, but I hope this is another clue to the (initramfs) prompt and failure to install.  Like shozzbott, I successfully installed 8.04 on my secondary drive, but on trying to reinstall it OR on trying to install 8.10 I get the busybox (initramfs) prompt with no erroe mesages preceeding it.  Between the successful install and the failure to install either version (about 3 days) I changed the boot order and installed an updated bios, then changed the boot order back. 

8.04 still runs OK and XP on my primary drive still runs OK.

---

### Post by MKlemm on 2008-11-03
> **amgalitz said:**
> Yes, the SATA links being down is a message I see also. Thanks for pointing out "dmesg", I missed that it was available at the initramfs prompt. I'll check output when I get home tonight. I'm new at this type of trouble shooting. shozzbott above is having similar issue with INTEL chipset, not good. This may be worth a bug report, but I've never done one so wish to investigate this further. I still may just search for an AMD2/AM2+ board that someone has got working and exchange. I have real work to do!

Yes, it's also an INTEL chipset in my machine, MSI 965P Neo2 mainboard, Intel 965 chipset (ICH8 aka 82801H southbridge).

When I boot with my "old" (from 8.04) kernel, which is version 2.6.24-19-generic, I see in dmesg output how my harddrive and my DVD are recognized on SATA interfaces 1 and 2 (ata1: ... and ata2:)
The output from dmesg at the initramfs prompt looks quite the same, but only instead of ata1: .... <device name>
it just says "ata1: SATA link down" and "ata2: SATA link down"

So, I gather that the drivers are all loaded and more or less running, but they don't see any of may devices, for whatever reason...

---

### Post by MKlemm on 2008-11-03
> **amgalitz said:**
> Yes, the SATA links being down is a message I see also. Thanks for pointing out "dmesg", I missed that it was available at the initramfs prompt. I'll check output when I get home tonight. I'm new at this type of trouble shooting. shozzbott above is having similar issue with INTEL chipset, not good. This may be worth a bug report, but I've never done one so wish to investigate this further. I still may just search for an AMD2/AM2+ board that someone has got working and exchange. I have real work to do!

Yes, it's also an INTEL chipset in my machine, MSI 965P Neo2 mainboard, Intel 965 chipset (ICH8 aka 82801H southbridge).

When I boot with my "old" (from 8.04) kernel, which is version 2.6.24-19-generic, I see in dmesg output how my harddrive and my DVD are recognized on SATA interfaces 1 and 2 (ata1: ... and ata2:)
The output from dmesg at the initramfs prompt when booting with the 2.6.27 kernel looks quite the same, but only instead of ata1: .... <device name>
it just says "ata1: SATA link down" and "ata2: SATA link down"

So, I gather that the drivers are all loaded and more or less running, but they don't see any of may devices, for whatever reason...

---

### Post by amgalitz on 2008-11-04
Thanks for helping!:grin:

Please be aware I have done over a half dozen installs of 8.10 in various ways and with different CD's and CD images (all check summed and checked) to figure this issue out](*,). I've tried installing with only one HDD in the system and still get the error, with IDE/PATA or SATA. I thought this would rule out GRUB vs linux drive confusion. I've used the GRUB menu to change the GRUB root options during actual boot up.

Current hardware configuration
[INDENT]IDE1 Master: 120G IDE/PATA, sdb by ubuntu
IDE1 Slave: empty
SATA1: CDROM
SATA2: 1TB HDD, sda by unbuntu, the current boot/system drive[/INDENT]

*OK, from the livecd as you asked:*
--------------
ubuntu@ubuntu:~$ [FONT="Lucida Console"]**sudo fdisk -l**

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00085e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+  83  Linux
/dev/sda2             609         669      489982+  82  Linux swap / Solaris
/dev/sda3             670      121601   971386290    5  Extended
/dev/sda5             670       43221   341798908+  83  Linux
/dev/sda6           43222       85773   341798908+  83  Linux
/dev/sda7           85774      121601   287788378+  83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3b9f3b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+  83  Linux
/dev/sdb2            1217        2432     9767520   83  Linux
/dev/sdb3            2433        3648     9767520   83  Linux
/dev/sdb4            3649       14593    87915712+   5  Extended
/dev/sdb5   *        3649        3672      192748+  83  Linux
/dev/sdb6            3673        3794      979933+  82  Linux swap / Solaris
/dev/sdb7            3795       14593    86742936   83  Linux[/FONT]
---------------
[I]What are these for:

**sda** : future data disk for file storage/serving, images, audio, video and acronis backups imagefiles from the two working WinXP Desktop machines.
**sda1**: Current root/boot partion, a small partion to hold a test root partion for ubuntu. this holds the currently installed unbuntu intrepid. I figured since ubuntu insisted on this being the first HDD, I'd try installing a system on it. My error messages come from this.
**sda2**: swap for the current temp installaton
**sda4**: don't know what happened to this one
**sda5,6,7**: data partions, see the labels in blkid listing for purpose.

**sdb** : is the PATA HDD that will hold upto 3 installations of ubuntu OS and shared /home
**sdb1: sdb2 and sdb3**. will be the root partitions of the different ubuntu or perhaps debian installations. One for production, One for production backup and one for testing new release. No valid system installed there just yet as I erased the partition to try a temporary installation on sda1.
**sdb5**: is a small partition to become a grub partition and hold an initial boot menu. I have this setup working on my Desktop working A8N-E based system (WinXP, Ubuntu 8.10 and 8.04 all working)
**sdb6**: future swap
**sdb7**: future sharted /home
[/I]
----------------
ubuntu@ubuntu:~$ **sudo blkid**
[FONT="Lucida Console"]/dev/sda1: LABEL="SATA1-1" UUID="1113a16f-e2f6-41ff-a02f-adbee660b738" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="276c4f7a-f5b4-4d58-b815-b6b35261be6f" 
/dev/sda5: LABEL="data1" UUID="06cb8667-e612-4938-8c0a-0afe8b67e1d0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="audio1" UUID="27dda38d-5705-4be6-8b55-7e627e289a12" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="daily" UUID="c4330d74-2f3f-476c-acd6-208294cb7820" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="ubuntu1" UUID="015b82e1-c57c-48f4-a1bf-70eddf40fd47" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: LABEL="ubuntu2" UUID="8775eb70-0ead-4a77-abb6-ab548dcebc32" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: LABEL="ubuntu3" UUID="6420454b-524f-4a94-8681-d39ffd237232" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: LABEL="gpart" UUID="96ce4b10-f83e-41c6-a1b0-5e1602a3c876" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="70551857-c845-40a8-877c-3e3e960f6e08" 
/dev/sdb7: LABEL="home1" UUID="a40fa1ad-8018-4065-a9ca-80f59b694328" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" [/FONT]
------------------
*Thought you might also like this::*
root@ubuntu:/sda1/boot/grub#** cat device.map**
(hd0)	/dev/sda
(hd1)	/dev/sdb
--------------------------
[I]I can't find a /target on the livecd session, but I mounted the root partition for the installed system.
------------------[/I]
**/sda1/boot/grub/menu.lst**  *(this is the installed system root/boot partition)*
............ [I]non relevant lines ommitted to save space
note that I edited this menu.lst during troubleshooting from the livecd session and then rebooted several times [/I]
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
*.... lines ommitted*
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		/dev/sda1 ; this changed force the root/boot partition
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro pci=nomsi iommu=noaperture all_generic_ide floppy=off irqpoll splash ;these options added to attempt to fix boot errors
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1113a16f-e2f6-41ff-a02f-adbee660b738
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1113a16f-e2f6-41ff-a02f-adbee660b738 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1113a16f-e2f6-41ff-a02f-adbee660b738
kernel		/boot/memtest86+.bin
quiet
---------------

Would you like anything from the initramfs session dmesg after boot?

cheers

alan

---

### Post by MKlemm on 2008-11-04
So you're able to boot from the 8.10 boot cd?
I can't even do that!
The problem is exactly the same, no matter if booting from the cd or from HD...

---

### Post by damien_d on 2008-11-04
I too, unfortunately, am having similar issues.

Hardware:
CPU: AMD Phenom X4 9950
Motherboard: Gigabyte M750SLI-DS4 (revision 1.0), chipset = nForce 750a
Graphics: NVidia 7300GT + Nvidia 8600
HDD = 1x320 SATA, 1x1TB SATA

Description of issues:
Was running 8.04 without issues, dual boot with WinXP (on which I am writing now)
Upgraded via update-manager -d, which is where the problems started.

With the default kernel with 8.10, I get the kernel issues as described in the previous posts - I will post pictures of the screen output soon.

I can drop back to my 2.6.24? (?? need to check ?) kernel that was with 8.04, and it boots nicely, but to drops back to low graphics mode and cannot reconfigure (suspect new X server issues there).

When attempting to run off the live 8.10 CD, I get the same kernel issues as noted in the previous posts.

This is all x86_64 (AMD64).  I have not attempted to load an i686 version in any case listed.

Hope this adds information to the problem.

---

### Post by Magnes on 2008-11-04
> **MKlemm said:**
> So you're able to boot from the 8.10 boot cd?
I can't even do that!
The problem is exactly the same, no matter if booting from the cd or from HD...

Maybe your CD-ROM is SATA and his is IDE?

I have identical problem. I have a mainboard with nforce I suppose (for Athlon X2). I can log in using older kernel but X not always works (some problem with nvidia driver). I'm considering "downgrade" (reinstalling 8.04) because a lot more things doesn't work for me (my mouse, my tablet, amarok has lags...).

Here is a bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/33269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/33269)

I had this problem from time to time on Ubuntu 8.04 when I had additional SATA drive plugged in. When I unplugged it, the problem stopped occuring. (sorry for my English)

---

### Post by damien_d on 2008-11-04
> **damien_d said:**
> I too, unfortunately, am having similar issues.

<snip> 

This is all x86_64 (AMD64).  I have not attempted to load an i686 version in any case listed.



I am now currently using the i686 8.10 liveCD.  It boots 2.6.27-7-generic without a problem.

For those that are smarter than me, see the following link for the dmesg output: [http://www.pastebin.ca/1244699](http://www.pastebin.ca/1244699)

Who else can use i686 but x86_64 (AMD64) causes problems?

Also, as previously promised, I have attached pictures of what the boot process is displaying

---

### Post by beatman on 2008-11-04
Hi All,
Just thought,I'd add my my story of woe....
First of all I am very new to Ubuntu... but used earlier versions for a couple of weeks... anyway With 8.10 now available I wanted to see how things are progressing...  My PC is fairly new, does not have IDE so SATA only...
Anyway downloaded the 386 image and burned it to CD... tried the Live boot demo OK.. and then tried to run the WUBI version to run within Vista. The WUBI loads OK and starts to install but half way into the install I have a message that say's cannot access the CD Drive (the one it has just been reading from ???) retry or cancel?

THIS IS CRAZY... WHO THE HELL RELEASED THIS...  !!!!

Oh well back to Windows for another 6 months.
Good luck you guy's

---

### Post by SpinningAround on 2008-11-04
Also got (I guess) the same problem, strange part is that I did use the beta release and it worked but the official release don't. 

Is there some way to gain access to a log file with the text shown in the attachments using LiveCD or similar since I'm not able to boot into ubuntu atm.

---

### Post by MKlemm on 2008-11-04
The problem still persists for me, however I think I can help you with getting 8.10 to Run on the older 2.6.24 kernel with Nvidia driver.
Here is what I did:
- moved the 2.6.24 entries in /boot/grub/menu.lst to the top of the file, before the 2.6.27 entries
- installed thelatest nvidia driver (177)
- replaced the script /etc/init.d/Linux-restricted-modules-common with an empty file. This script was setting up a tmpfs under the kernel module tree in 8.04 andcopying way too old NVidia kernel modules in it. By removing this file, the new DKMS system willbe able to do it's job and copy a newly compiled version from 8.10 into the modules tree.

---

### Post by psusi on 2008-11-04
It looks like these other folks are having errors communicating with their hard disk.  Amgalitz, do you see any similar ata error messages?  And yes, the output of dmesg might be helpful.

Could everyone check their bios settings and make sure the sata controller is set to AHCI mode?

---

### Post by MKlemm on 2008-11-04
> **psusi said:**
> It looks like these other folks are having errors communicating with their hard disk.  Amgalitz, do you see any similar ata error messages?  And yes, the output of dmesg might be helpful.

Could everyone check their bios settings and make sure the sata controller is set to AHCI mode?

I'll try to capture the dmesg output somehow via an USB stick if I manage to mount it from initramfs

As to AHCI mode, I am afraid I  must say that there is none on my board. My sata controllersupports IDE mode only.

---

### Post by MKlemm on 2008-11-04
psusi - hope I'm not keeping you too much from the important elections in your country today :-)

I managed to mount a USB stick when booting the live CD fails (that BusyBox rules!), and I put the dmesg output here as an attachment.

The "sda" you see in there as being initialized correctly is just the USB stick, though, the hard disks and optical are still unavailable, as you can see in the lines 443, 445, 460, and 464, where it says "SATA link down".

As a comparison, I attached the dmesg output from my still working 2.6.24-19-generic setup, and if you look in there (lines 282 through 287) you can see that both my harddisk and optical drive get initialized correctly as ata3 and ata4, respectively.

These entries seem to be the only relevant difference in the dmesg output Ic an see, there are the same ACPI errors in both the working 2.6.24 and the broken 2.6.27 setups, and besides that, there don't seem to be any ATA/SATA related error messages.

Additionally, I attached the output from lspci, to give a more detailed picture of my hardware...
Hope anyone can help with this information.

---

### Post by jimbudler on 2008-11-04
I have exactly the same problem. IBM Intellistation Z Pro with SATA drives.

At initramfs prompt:
ls /dev/disk/by-uuid showed the correct UUID entries.
mounted the disk, checked fstab, correct UUID.
checked grub menu.lst, correct UUID.
 
Typed exit. The system continued to boot correctly.

Obviously a timing issue with the with the 2.6.27 kernel.

Tired of playing with it, I set grub to boot with the 2.6.24 kernel and it works fine.

jim

---

### Post by amgalitz on 2008-11-04
Ok, thanks to all for helping (figure that can't be said too much).
psusi: I'm at work without access to system but my SATA and IDE links were not working. Boot system was throwing multiple sata link error messages about 'slow response' etc.

I've been googling and see many people with different hardware have issues with controllers that have both IDE and Sata channels. There seems to be a major bug here. I don't understand how I can boot to a fully working session with the liveCD with full access to all my drives, but the installed system crashes. Somewhere there are good drivers/modules!

I've also seen that for Asus MB's people have had success with using the "F6" key at the early phase of boot up which allows passing boot options. See my first post for some of these. It may be that one must set AHCI on for the SATA controller, then pass the boot options WHEN STARTING THE LIVECD session that does the installation. I saw a post that implied if you install off a liveCD with different boots options than what the final installation will run, that can cause the initialization of the IDE/SATA channels to fail. 

To answer psusi's other question, I did try switching my SATA mode to AHCI, but this was after the system was built and installed. It may be that the system needs to be built with AHCI ON to begin with. (Insert expert help/advice here <G>)

I will be testing this out tonight with yet another 'scorched' earth install. I just am not sure which combination of the boot options makes sense. I thinke all_generic_ide, iommu=noaperture (for 4GB of RAM in 64b system), pci=nomsi  will be my first attempt. suggestions anyone?

I'm close to giving up on this mb and have ordered an ASUS M3N78-PRO [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131320](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131320). I don't like it as well since the S/PDIF Out is only Coaxial but I can live with that and people have made it work it seems. I have an AMD66 4850e and two sticks of 2g match 1066 Ram (yes, the 4850e only does 800, but thinking ahead). I looked but did not fing a thread about recommended MB for the AM2/AM2+ socket

I'm also thinking of trying a DFI LP based on the 790 chipset [http://www.newegg.com/Product/Product.aspx?Item=N82E16813136056](http://www.newegg.com/Product/Product.aspx?Item=N82E16813136056), but can't find any reports either good or base. I don't need the graphics as I have an ASUS 9600GT silent already but I want optical sound out and 6 sata.

All in all I think this current installation iso is not at all ready for prime time. How do we go about reporting this as a bug. no way are these gymnastics appropriate for an OS for "everyone". The boards involved are not unusual choices.

cheers all

---

### Post by psusi on 2008-11-04
mklem: have you tried using the pci=nomsi boot option?

amgalitz: yes, you need to install the system in AHCI mode, switching it after will cause problems.

---

### Post by MKlemm on 2008-11-04
As I've collected a fair amount of information about the issue now - although the symptoms seem to be somewhat different for all of us - I'm going to try to file a bug report in launchpad.

I also think this situation isn't acceptable for a production release. My hardware really isn't anything exotic, in fact it seems to be a fairly common setup, and it has worked with the 2.6.24 kernel. There should be a possibility to do something about it...

---

### Post by MKlemm on 2008-11-04
> **psusi said:**
> mklem: have you tried using the pci=nomsi boot option?

Thank you for that hint, I just tried, but it didn't change anything :-(

---

### Post by OriginalGrumpyOldMan on 2008-11-04
I'm not technically savvy enough for some of the more advanced error-proding, but for what it's worth: I'm using a PC Chips M848A v.5 mobo with a recycled Athlon 2400 and 1 gb of ram, using the standard IDE channels for boot drives & DVD burner. The add-on PCI SATA controller is a RocketRAID 1640, with 4 single drives attached (no raid). It's been mostly my cheap reliable file server for a while now, with a some low-end usage (surf web, write docs etc.)

When booting normally (Feisty at this point, but also Gutsy boot CD), it doesn't matter if the attached drives are active or not, and in GParted, my 2 boot / IDE drives show up as hda and hdb, and the extra SATA drives, if available, as hde etc.

But when booting Intrepid, it only works with all drives active, and in GParted they will show up as sda, sdb, sdc, sdd, sde, sdf, the 2 last ones now being my prior hda and hdb. To it's credit it works, but I don't know how it would affect samba etc., and more importantly since the some of the SATA drives are only for the occasional backup I'd really like to turn them off/on selectively...

(BTW, when it doesn't work, it doesn't matter if they are simply turned off in their drive cage or physically disconnected)

---

### Post by Nashova on 2008-11-04
> **amgalitz said:**
> HPROBLEM. Initial boot after install throws this error:
_____________________
[INDENT][FONT="Fixedsys"]Boot from (hd0,0) ext3  *** *[FONT="Arial"];*** = UUID for partition omitted, ag[/FONT]*
Starting up ...
[   0.004000] Aperture pointing to e820 RAM. Ignoring.
[   0.004000] Your BIOS doesn't leave a aperture memory hole
[   0.004000] Please enable the IOMMU option in the BIOS setup
[   0.004000] This costs you 64 MB of RAM
Loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/*** does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/FONT][/INDENT]
--------------
output of 'cat /proc/cmdline':
 **root=UUID=*** ro quiet splash ;note** *** is the above UUID



A friend found the problem and the solution to this error on Intrepid Ibex.
The problem isn't the HD or the drivers, it is the timing. It means that when you start Ubuntu the sda mount is slower than the system.
to fix this you have to set a rootdelay in the file /boot/grub/menu.lst
It can be done from the live cd when it finishes the installation, click on the continue usin the liveCd and open a terminal
use the next commands:
```
$ sudo -s
```
sdaX is the HD where is located root "/"
```
# mount /dev/sdaX /mnt 
```
Now edit the file menu.lst
```
vi /mnt/boot/grub/menu.lst
```
in there find the line that say:
```
"kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=**** ro quiet splash"
```
And add the command "rootdelay=40"
It looks like this:
```
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=**** ro quiet splash rootdelay=40
```
After that save the file and restart the PC
That way you can have that problem solved

In a upgrade from 8.04 to 8.10 you can do the same before the system restart, you just don't have to mount root.
```
$ sudo -s
vi /boot/grub/menu.lst
```

If this don't works increment the value of rootdelay.

I have solved this problem in two PC's till now. thanks to mi friend.
I hope this works for all of you.

---

### Post by SpinningAround on 2008-11-04
> **MKlemm said:**
> psusi - hope I'm not keeping you too much from the important elections in your country today :-)

I managed to mount a USB stick when booting the live CD fails (that BusyBox rules!), and I put the dmesg output here as an attachment.

The "sda" you see in there as being initialized correctly is just the USB stick, though, the hard disks and optical are still unavailable, as you can see in the lines 443, 445, 460, and 464, where it says "SATA link down".

As a comparison, I attached the dmesg output from my still working 2.6.24-19-generic setup, and if you look in there (lines 282 through 287) you can see that both my harddisk and optical drive get initialized correctly as ata3 and ata4, respectively.

These entries seem to be the only relevant difference in the dmesg output Ic an see, there are the same ACPI errors in both the working 2.6.24 and the broken 2.6.27 setups, and besides that, there don't seem to be any ATA/SATA related error messages.

Additionally, I attached the output from lspci, to give a more detailed picture of my hardware...
Hope anyone can help with this information.

Would you please explain how you manage to mount usb stick in initramfs?

---

### Post by amgalitz on 2008-11-05
Nashova, thanks for the suggestion, however, I'VE SOLVED THE PROBLEM, at least most of it.

I removed the LG GGC-H20-L SATA Blu-ray/HD DVD/DVD/CDROM from SATA1
Moved the WD 1TB HDD to SATA1
Pulled from another system an old Plextor PATA CDROM on the IDE Slave spot
Left the PATA/IDE WD120G HDD on Master
(Note, I believe I had tried the LG Optical on SATA2, and the WD1TB on SATA1 and the SATA config on AHCI, but hard to remember)
 
In the Asus M3A78 bios 
```
Main|SATA Configuration: changed SATA => AHCI. 
Power|ACPI Support [Disabled]  (default)
Power|ACPI APIC support [Enabled] (default) *Note: when I disabled this option the system boot hung at bluetooth in during the Hardware Abstraction*
``` 
Everything else left at default.

Booted livecd session 8.10 AMD64 Desktop
Erased first partion on the WD120G
Installed into new first partition on WD120G
Rebooted
Now have working Intrepid from WD120g (PATA/IDE) showing as sd[SIZE="3"]b[/SIZE]
Overall dramatic increase in boot up both at post, bios and OS level.:biggrin:

```
# blkid
/dev/sda1: LABEL="ubuntu1-WD1TB-1" UUID="1113a16f-e2f6-41ff-a02f-adbee660b738" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="276c4f7a-f5b4-4d58-b815-b6b35261be6f" 
/dev/sda5: LABEL="data1" UUID="06cb8667-e612-4938-8c0a-0afe8b67e1d0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="audio1" UUID="27dda38d-5705-4be6-8b55-7e627e289a12" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="daily" UUID="c4330d74-2f3f-476c-acd6-208294cb7820" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="4e5a2451-f781-4c95-9b77-47dc774adc66" TYPE="ext3" LABEL="ubuntu1-WD120G" 
/dev/sdb2: UUID="e7e70184-cf5e-49af-9bcf-55635abda69f" TYPE="ext3" LABEL="ubuntu2-WD120G" 
/dev/sdb3: UUID="befab1d6-eab7-4ac8-a890-e343e599c2a2" TYPE="ext3" LABEL="ubuntu3-WD120G" 
/dev/sdb5: UUID="157558dd-ded0-4394-aca9-f0cdd132b0a6" TYPE="ext3" LABEL="gpart-WD120G" 
/dev/sdb6: TYPE="swap" UUID="70551857-c845-40a8-877c-3e3e960f6e08" 
/dev/sdb7: UUID="3341a8c1-5188-42ec-bd72-516fdc645cea" TYPE="ext3" LABEL="home-WD120G"
``` 

```
# cat /boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

partial /boot/grub/menu.lst
```

...
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs
...
# groot=4e5a2451-f781-4c95-9b77-47dc774adc66
...
# kopt=root=UUID=4e5a2451-f781-4c95-9b77-47dc774adc66 ro ...
...
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4e5a2451-f781-4c95-9b77-47dc774adc66
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4e5a2451-f781-4c95-9b77-47dc774adc66 ro iommu=noaperture rootdelay=40 splash 
initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4e5a2451-f781-4c95-9b77-47dc774adc66
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4e5a2451-f781-4c95-9b77-47dc774adc66 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4e5a2451-f781-4c95-9b77-47dc774adc66
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

```
# lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02
```

Interestingly, dmesg shows some errors, but boot still worked.
The SATA AHCI

```
[    2.576782] ahci 0000:00:11.0: version 3.0
[    2.576802] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.576941] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    2.576944] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.577988] scsi0 : ahci
[    2.579068] scsi1 : ahci
[    2.580231] scsi2 : ahci
[    2.580323] scsi3 : ahci
[    2.580412] scsi4 : ahci
[    2.580811] scsi5 : ahci
[    2.580924] ata1: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fff900 irq 22
[    2.580927] ata2: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fff980 irq 22
[    2.580931] ata3: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fffa00 irq 22
[    2.580934] ata4: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fffa80 irq 22
[    2.580937] ata5: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fffb00 irq 22
[    2.580940] ata6: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fffb80 irq 22
[    2.912542] usb 1-3: new low speed USB device using ohci_hcd and address 3[B]
[    3.068027] ata1: softreset failed (device not ready)
[    3.068033] ata1: failed due to HW bug, retry pmp=0[/B]
[    3.089423] usb 1-3: configuration #1 chosen from 1 choice
[    3.164735] usb 1-2.1: new full speed USB device using ohci_hcd and address 4
[    3.228227] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.229308] ata1.00: ATA-8: WDC WD10EACS-00D6B0, 01.01A01, max UDMA/133
[    3.229310] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.230664] ata1.00: configured for UDMA/133
[    3.271362] usb 1-2.1: configuration #1 chosen from 1 choice
[    3.564233] ata2: SATA link down (SStatus 0 SControl 300)
[    3.900240] ata3: SATA link down (SStatus 0 SControl 300)
[    4.236228] ata4: SATA link down (SStatus 0 SControl 300)
[    4.572225] ata5: SATA link down (SStatus 0 SControl 300)
[    4.908722] ata6: SATA link down (SStatus 0 SControl 300)
[    4.924310] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
[    4.925958] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    
```

Still getting the "aperture" error, but I will add iommu=noaperture to my kernel options (no such bios option on the M3A78) and see if that goes away.

```
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 20000000 size 32 MB
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Please enable the IOMMU option in the BIOS setup
[    0.004000] This costs you 64 MB of RAM
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.004000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.004000] Memory: 4046472k/4980736k available (3112k kernel code, 146928k reserved, 1575k data, 536k init
)
```

Next steps:
- try to fix the aperture error (annoying)
- plug SATA LG optical into SATA2, leave Plextor on IDE channel, see if that crashes the ACHI/SATA system.
- then pull the IDE optical and leave the SATA optical in. See if that crashes.
I don't have another SATA optical so can't test if any SATA optical will do this or is the LG different because it also has Blu-ray/HD DVD ability. ANYONE?

BTW before I got the system working, I tried pulling one Ram stick and running with a single 2BD. Major malfunction with that.

I'm still not happy that the PATA/IDE show up AFTER the SATA. Hopefully the partition LABEL feature will get ironed out so we can avoid UUID's. I kept a spare system HDD with a complete duplicate partition made with image duplication, to plug in if the system drive failed on the server. That won't work with UUID's without editing /etc/fstab, /boot/grub/menu.lst etc. Especially irksome once I've built the Grub partion and made multiboot menu, ](*,) 

Sorry about long post, but hope this might be helpful.
It's miller time...
cheers

):P

---

### Post by MKlemm on 2008-11-05
> **SpinningAround said:**
> Would you please explain how you manage to mount usb stick in initramfs?

Yes:
- Boot the system with an USB stick plugged in. It must be a "generic" USB stick (USB mass storage device), which doesn't need special drivers, and I think most of the USB sticks available are generic ones. Maybe an external USB hard drive will also work

- When the boot fails and drops to initramfs, enter 
cd /dev/disk/by-uuid
ls

and you will see a cryptically named device node file.
- Then, type "mkdir /mnt" to create a mount point
- Then do "mount <cryptical device node name> /mnt"
- then "cd /mnt", and you are on the USB stick.
- You can save the dmesg output by doing "dmesg >dmesg-out.txt"
- before you reboot, type "sync" just to make sure no data is lost.

---

### Post by amgalitz on 2008-11-05
Update:

Adding ```
iommu=noaperture
``` to kernel options in menu.lst fixed the 'no aperture' error during boot up.
For folks new to menu.lst editing:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4e5a2451-f781-4c95-9b77-47dc774adc66
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4e...66 ro **[COLOR="Red"]iommu=noaperture[/COLOR]** rootdelay=40 splash 
initrd		/boot/initrd.img-2.6.27-7-generic
```
```
rootdelay=40
``` does not seem to be needed on this system, but I added/left it in during testing just in case.

Added SATA LG optical back to SATA2 ports leaving PATA Plextor optical on slave IDE.
--> System booted up fine and even though I did not add anything into fstab, the LG optical got mounted and was usable. In fact I forgot a cd was in it and it's icon appeared on the desktop.

Next, pulled PATA Plextor out, leaving SATA LG.
--> crash to initramfs
However this may have been because I did not mark the Plextor as not installed in the bios.

Added PATA Plextor back into IDE slave, left SATA LG attached
--> System rebooted fine.

I next will install another 8.10 system, on the ubuntu2 partition with the current bios settings, but no PATA/IDE cdrom on the IDE slave spot and the LG SATA optical drive on the SATA2 spot. However that is for another day.

So question is any SATA optical going to do this or is the LG Blu-ray/DVD/CD optical enough non standard atapi that the current sata/ahci driver/module choking on it? Unfortunately I don't have a more standard SATA optical drive to test.

I also don't know what I need to do to my fstab to adjust for pulling out the Plextor PATA and leaving the SATA LG. That why I'll just try a fresh install into one of the empty spare partitions. that is what they are there for. ;-)

An optical drive on the SATA channel should crash the system IMHO so this may be worth a separate thread and perhaps bug report once the exact details are worked out. Can anyone reproduce this?

---

### Post by MKlemm on 2008-11-05
Well, I'm not happy with that solution at all since I don't want to plug in a PATA drive if I have a much better SATA setup, which worked fine in kernel 2.6.24, btw.
I also think the issues are somewhat different on your side, at least you see SATA-related error messages in your dmesg output, which in fact could mean that there is some hardware or firmware bug in your SATA optical drive.

For my part, however, I don't see any error messages besides that "SATA link down", so it is really hard to tell what might have been causing this...

Btw. I saw that there is already a bug filed which seems to be just what we are seeing here, however it was filed against an earlier version of ubuntu originally, but the kernel versions in the comments exactly match my experience...

---

### Post by psusi on 2008-11-05
Amgalitz, can you tell me which driver is being used for your controller?  Run lsmod | grep ata_ and post the results.

I'm trying to figure out how to get some more debug output to get an idea of what is wrong other than "link down", but I can't for the live of me remember how you enable KERN_DEBUG level printk output...

---

### Post by amgalitz on 2008-11-05
MKlemm: be aware I have not posted dmesg output from the crashed session, only from the successful one. I'll see if I can pull output onto a key drive as you suggested.
psusi: no problem, I'll grab the output from the working system also when I get home. It's up and running for general burn in now.
> I can't for the live of me remember how you enable KERN_DEBUG level printk output...Yeah, well at least you know it is possible!!

You know, I almost installed off the IDE Plextor before getting the SATA LG! I'd have had a working 8.10 system in < 30 min on SATURDAY morning. I thought I'd save the time of removal, installing, removal and reinstalling the drive; ARRRGGGGH. Then I would have known right away the root cause. Oh well, lesson I guess is start with plain vanilla first, then get exotic.

cheers and thanks again. be back with update soon.

---

### Post by amgalitz on 2008-11-05
```
lsmod | grep ata_ 
pata_atiixp            14208  8 
ata_generic            14212  0 
pata_acpi              13568  0 
libata                200160  4 pata_atiixp,ata_generic,pata_acpi,ahci
```

---

### Post by amgalitz on 2008-11-06
Update: I could not get mounting of the USB stick to work in the initramfs. I got either invalid argument or file/directory.

In any case, perhaps this might not an Intrepid problem but rather a BIOS bug in the M3A78 or firmware in the LG optical. However, that the livecd will boot a fully operational session with access to all the drives and partitions suggest that the problem is in the installation.

The only way the system boots with the SATA LG optical drive installed is if TWO IDE devices are present on the IDE channel. I tried adding a second IDE/PATA HDD on the Slave IDE spot and the system booted right up fine. So either a HDD or Optical Drive is needed. Of note is that the Post is much faster with both IDE spots filled. Perhaps this is just because the slave position doesn't have to time out.

BTW, this is how the IDE and SATA HDDs are performing:
```
@aglx2:~$ sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   2506 MB in  2.00 seconds = 1253.96 MB/sec
 Timing buffered disk reads:  282 MB in  3.02 seconds =  93.37 MB/sec

@aglx2:~$ sudo hdparm -Tt /dev/sdb
/dev/sdb:
 Timing cached reads:   2448 MB in  2.00 seconds = 1224.55 MB/sec
 Timing buffered disk reads:  144 MB in  3.03 seconds =  47.48 MB/sec

@aglx2:~$ sudo hdparm -Tt /dev/sdc
/dev/sdc:
 Timing cached reads:   2538 MB in  2.00 seconds = 1269.43 MB/sec
 Timing buffered disk reads:  152 MB in  3.01 seconds =  50.44 MB/sec

```
In case this helps 
```
@aglx2:~$ sudo hdparm -I /dev/sda
/dev/sda:
ATA device, with non-removable media
	Model Number:       WDC WD10EACS-00D6B0                     
	Serial Number:      WD-WCAU42637752
	Firmware Revision:  01.01A01
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
...
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	    	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	Segmented DOWNLOAD_MICROCODE
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	SATA-II signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	    	DMA Setup Auto-Activate optimization
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
...
```
 

Cheers

---

### Post by psusi on 2008-11-06
Hrm.. looks like you have a few different ata controllers.  Can you get the output of lshw?

---

### Post by amgalitz on 2008-11-06
Ok, Here is output of 
```
lshw
```
it is a bit long (It was too big to attach as a file!):

```
aglx2
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=40639A52-E9FE-D511-9BFE-002215B7D19B
  *-core
       description: Motherboard
       product: M3A78
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: MF7087G03204863
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0703 (10/15/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Dual Core Processor 4850e
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) Dual Core Processor 4850e
          serial: To Be Filled By O.E.M.
          slot: AM2
          size: 2500MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 3a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RX780/RX790 Chipset Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G94 [GeForce 9600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port C)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:22:15:b7:d1:9b
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.16 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk
                description: ATA Disk
                product: WDC WD10EACS-00D
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAU42637752
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00085e89
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 1113a16f-e2f6-41ff-a02f-adbee660b738
                   size: 4769MiB
                   capacity: 4769MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-02 10:04:06 filesystem=ext3 label=ubuntu1-WD1TB-1 modified=2008-11-05 20:01:50 mounted=2008-11-05 01:25:22 state=clean
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 276c4f7a-f5b4-4d58-b815-b6b35261be6f
                   size: 478MiB
                   capacity: 478MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 926GiB
                   capacity: 926GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 325GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 325GiB
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 274GiB
           *-cdrom
                description: DVD-RAM writer
                product: BDDVDRW GBC-H20L
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 1.B0
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi6
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp
           *-disk:0
                description: ATA Disk
                product: WDC WD1200BB-00D
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@6:0.0.0
                logical name: /dev/sdb
                version: 15.0
                serial: WD-WMAEK2913271
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f3b9f3b9
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@6:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 4e5a2451-f781-4c95-9b77-47dc774adc66
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-04 20:07:51 filesystem=ext3 label=ubuntu1-WD120G modified=2008-11-05 22:07:41 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-11-05 22:07:41 state=mounted
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@6:0.0.0,2
                   logical name: /dev/sdb2
                   logical name: /ubuntu2
                   version: 1.0
                   serial: e7e70184-cf5e-49af-9bcf-55635abda69f
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-04 20:07:58 filesystem=ext3 label=ubuntu2-WD120G modified=2008-11-05 22:07:42 mount.fstype=ext3 mount.options=rw,noatime,relatime,errors=continue,data=ordered mounted=2008-11-05 22:07:42 state=mounted
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@6:0.0.0,3
                   logical name: /dev/sdb3
                   logical name: /ubuntu3
                   version: 1.0
                   serial: befab1d6-eab7-4ac8-a890-e343e599c2a2
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-04 20:08:04 filesystem=ext3 label=ubuntu3-WD120G modified=2008-11-05 22:07:42 mount.fstype=ext3 mount.options=rw,noatime,relatime,errors=continue,data=ordered mounted=2008-11-05 22:07:42 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@6:0.0.0,4
                   logical name: /dev/sdb4
                   size: 83GiB
                   capacity: 83GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /gpart
                      capacity: 188MiB
                      capabilities: bootable
                      configuration: mount.fstype=ext3 mount.options=rw,noatime,relatime,errors=continue,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 956MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sdb7
                      logical name: /home
                      capacity: 82GiB
                      configuration: mount.fstype=ext3 mount.options=rw,noatime,relatime,errors=continue,data=ordered state=mounted
           *-disk:1
                description: ATA Disk
                product: WDC WD800JB-00ET
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@6:0.1.0
                logical name: /dev/sdc
                version: 77.0
                serial: WD-WCAHL6708725
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=41b3a1bf
              *-volume
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@6:0.1.0,1
                   logical name: /dev/sdc1
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdc5
                      logical name: /media/AGXP1_E
                      capacity: 74GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: 1
          bus info: usb@6:1
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdd
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sde
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:9b:23:84:aa:c3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Current setup:
  MB        : ASUStek M3A78 (bios 703=latest)
  CPU       : AMD64 X2 4850e
  Memory    : 2 x 2GB OCZ 1066
  IDE Master: WD 120GB HDD
  IDE Slave : WD  80GB HDD
  SATA1     : WD   1TB HDD SataII
  SATA2     : LG GBC-H20Li  BD/DVD/CD optical drive
  SATA3-6   : empty
  Video     : ASUStek 9600GT silent PCIe 2.0x16

---

