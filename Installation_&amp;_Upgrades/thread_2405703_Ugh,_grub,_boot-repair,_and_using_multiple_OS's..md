---
title: "Ugh, grub, boot-repair, and using multiple OS's."
date: 2018-11-09
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2018-11-09
Something is amiss. Depending on where or how I look, where I run update-grub, or how I run boot-repair, I get different 'information' and defaults.

But I know the following has happened...

I have multiple partitions with multiple OS's (currently, all Ubuntu based) on an SSD.
Let's call the disk nvme, and the partitions nvme_p[1-6].

[B]a) If I load a new OS, the default location for grub is nvme, and that's what I select.
b) If I run boot-repair, it does not allow me to place grub in nvme, rather it wants me to place it in nvme_p1, the /boot/efi partition, and I'VE DONE THAT ALSO.[/B]
So, I've done BOTH (a) & (b). Which is likely the root of my problem.

How do I fix this? How do I get boot-repair to load grub where all the other OS's load grub when I install an OS?

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

Here is a post from Oldfred which may help you.

[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

In one post he suggested not to use auto repair, rather asked a few details from the logs.

> Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
You can run this script with terminal & post its output to pastebin  site. It is part of Boot-Repair's report, but Boot-Repair shows a lot  more info.
       Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

Copy pasted from his post.

Regards,
Mitesh

---

### Post by Dennis N on 2018-11-09
The Ubuntu installer (not used by Lubuntu) installs grub to the efi system partition (nvme_p1) even though the selector on the partitioning page defaults to a drive name (which in you case I assume is nvme). You cannot select where grub files are installed - that option is disabled. 

paragraph (b) should produce the same result.

---

### Post by aeronutt on 2018-11-09
^ Thanks, so that's important to know!

So, I ran boot-repair. Apparently successfully as I see all the OS's when the grub menu pops up, and am able to boot and log in (I haven't logged in to all the OS's yet). But.

Here's the oddity.  If I hit F12 while booting, I get a list of OS's that I haven't had loaded in 6 months or more. Fedora, and Neon. And those do NOT show up in the grub menu.

[https://i.imgur.com/HpVFy8Z.jpg](https://i.imgur.com/HpVFy8Z.jpg)

---

### Post by oldfred on 2018-11-09
Please do not post screenshots or photos in line. Not everyone has highspeed Internet.
You can easily attach screenshots with Forum's advanced Editor and paperclip icon.

       If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 
    
UEFI remembers old installs. It only erases entries if you disconnect drive.
You can use efibootmgr to manage UEFI boot entires or your UEFI.
See also 
man efibootmgr

Some entries like Windows UEFI may add back in when you reconnect a drive by looking at all the /EFI/xxxx folders in the ESP.

Boot-Repair's report does not show all the details on NVMe drives. It uses bootinfoscript as first part of report & it does not yet include NVMe drives.
       Support NVMe and MMC devices bug oldfred request
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues) 
    I do not have NVMe drive & author needs someone to test changes to bootinfoscript with NVMe drive.

See also post #2 above. :)

---

### Post by Dennis N on 2018-11-10
You probably already know all this, but here's what goes on:

Each OS creates a different grub menu (from the other OSes) when you run sudo update-grub from it. Each OS puts itself first, then looks around for other OS to add entries for after that. 

Which grub menu appears when you boot the computer depends on the UEFI boot order*. The OS which is first in the UEFI boot order is the one whose grub menu you get on startup. 

*the command **sudo efibootmgr** run from the terminal will reveal the UEFI boot order. Normally, the last OS installed is first. But, you can use the efibootmgr command with -o option to change the order.

---

### Post by aeronutt on 2018-11-10
ahhh....efibootmgr, something I was not aware of, thanks!

So, everytime I think I kinda know what grub does, I prove myself wrong.

Is there a layman's description of how grub manages multiple OS's, and what happens when one runs update-grub from 2 different OS's?

I need pictures! lol

Thanks for the help.

---

### Post by oldfred on 2018-11-10
Do not have pictures, but I currently have 4 or 5 Ubuntu installs, but have not finished Disco since they fixed installer.

Each wants to update, but I maintain one as main working install, backup ESP, so I can restore it when one of my other installs changes it.
On main working install I turn off os-prober and add my own entries in 40_custom, otherwise the update-grub takes a while to scan all the installs.

There is a way to install without grub, have not tried it recently, but then you have to add entry to working version of grub in another install, either os-prober with sudo update-grub or manually in 40_custom.

       If you do not want grub installed from live installer:
sudo ubiquity -b
[http://askubuntu.com/questions/838450/how-can-ubiquity-be-forced-not-to-install-grub/838527#838527](http://askubuntu.com/questions/838450/how-can-ubiquity-be-forced-not-to-install-grub/838527#838527)

UEFI version of grub runs efibootmgr and adds a new entry and makes it first in boot order.

I have tried renaming my install in /etc/default/grub and grub does create new folder in ESP, new entry in UEFI. But something in grub/shim file is hard coded to use /EFI/ubuntu/grub.cfg, so only that file is actually used for booting.

UEFI uses GUID of your ESP - efi system partition, both of these entries really boot main install since it uses /EFI/ubuntu/grub.cfg.
```

fred@Bionic-Z170N:~$ sudo efibootmgr -v
[sudo] password for fred: 
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0014,0015,0013
Boot0000* ubuntu    HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* bionic_18_04    HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\BIONIC_18_04\SHIMX64.EFI)
```

This uses UUID of you install. Rather trhan reinstall grub from main working install on sda (hd0), I just edited it to have correct UUID, drive & partition.
```

fred@Bionic-Z170N:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
#search.fs_uuid 75f5141c-8bab-4168-8855-4bf000406680 root hd1,gpt5 
search.fs_uuid c29fc361-ea05-420b-b919-850aeef65dd4 root hd0,gpt4
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by aeronutt on 2018-11-10
> **oldfred said:**
> ...
       If you do not want grub installed from live installer:
sudo ubiquity -b
[http://askubuntu.com/questions/838450/how-can-ubiquity-be-forced-not-to-install-grub/838527#838527](http://askubuntu.com/questions/838450/how-can-ubiquity-be-forced-not-to-install-grub/838527#838527)
...


!!!!! THIS  is what I've been looking for. I have not been happy since they removed the 'advanced' options from the live installer GUI that allowed you to install without (re)loading grub. Didn't know I could launch with that option turned off. I'll definitely try this next time, it's the way I prefer.

Thanks!!!

---

### Post by aeronutt on 2018-11-19
So, I have a followup question...

I have 2 disks. One is now all data (it USED to have OS's on it), and the other disk is 5 partitions of EFI + OS's.

I just installed another "test" OS on one of the partitions of my OS disk.

And low and behold, EFI bootmanager yet again seemed to look at my data disk, see that it at one time LONG ago had Fedora on it, and put it FIRST in line to boot from. Ug.

Is there any way to permanently "remove" the fact that my data disk at one time had (several) OS's loaded on it? Is there some flag, or sector on my data disk that has this 'history'?
(I had recently run efibootmgr and deleted "fedora" from the list, but it has not popped back up.)

---

### Post by oldfred on 2018-11-19
You have UEFI which is a boot manager (menu) and grub which is both a boot manager & boot loader.

UEFI remembers its entries and you can delete with efibootmgr.
But it may find entries in The ESP at /EFI/.... , if you have removed an install, you can remove that folder in the ESP.

Or if Fedora still has a /boot partition or boot files, grub2's os-prober will find that and add it to grub's boot menu.

I typically turn os-prober off as first thing. I have installs on both drives, some obsolete, but not yet deleted. The os-prober takes forever to scan all my installs and add them to grub menu. I just copy the installs I want with simplified boot stanza into 40_custom. The no more scans are required.
I used to use device, but plugging in flash drive changes my device list. I would manually edit grub boot stanza when it did not work as I remembered I had plugged in a flash drive. I now use labels. Or I use a configfile, if I want the full boot stanza from another install.

       Use labels:
[https://ubuntuforums.org/showthread.php?t=2076205&p=13783902#post13783902](https://ubuntuforums.org/showthread.php?t=2076205&p=13783902#post13783902)
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive) 

  ```
 menuentry "Ubuntu 19.04 Disco  (on /dev/sdb8)" {

 set root=(hd1,gpt8)
search --set=root --label disco --hint hd1,gpt8
configfile /boot/grub/grub.cfg 
 }     
```

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Configfile example
[https://ubuntuforums.org/showthread.php?t=2076205&p=13788092#post13788092](https://ubuntuforums.org/showthread.php?t=2076205&p=13788092#post13788092)

---

### Post by aeronutt on 2018-11-26
So a follow-up somewhat related question.
Assume all is well, and I have OS-1 and OS-2, where OS-1 is my primary and is the OS I want to manage grub from, run update-grub , etc.
But, if I do "sudo apt upgrade" in OS-2, if it updates its kernel, it uses its /etc/default/grub file and becomes the "primary" OS.
Is there a way around this?

---

### Post by Dennis N on 2018-11-26
> Assume all is well, and I have OS-1 and OS-2, where OS-1 is my primary and is the OS I want to manage grub from, run update-grub , etc.
But, if I do "sudo apt upgrade" in OS-2, if it updates its kernel, it uses its /etc/default/grub file and becomes the "primary" OS.
Is there a way around this? 

In UEFI, the grub menu you see at startup comes from the OS which is first in the UEFI boot order. That is your OS1. The grub menu entry in OS1 starts up the other OS. The grub in OS2 never runs at all.

When update-grub is run from OS2 by a kernel upgrade or manually, it does not change the UEFI boot order. It does change its own grub.cfg to put a newly-installed kernel first. But the grub menu from this grub.cfg is not normally used or seen during startup (or ever) and the grub in OS2 does not boot anything - even OS2 itself*. 

* there is an exception - you can transfer the booting of OS2 to its own grub if things are set up differently - that is called chainloading. But that is not the way most users multiboot Linux distros.

---

### Post by aeronutt on 2018-11-26
I must be 'accidentally' chain loading, because grub boot order is definitely changed when a kernel upgrade happens in OS2.
How would I go about fixing this?

---

### Post by yancek on 2018-11-26
Do you have your "OS" disk set to first boot priority in the BIOS?
Do you have your EFI partition on this same disk?
Does your system/systems boot from the EFI files on this disk?
Do you see Fedora listed when you run sudo efibootmgr?   You can delete that entry if you no longer have Fedora.

> I must be 'accidentally' chain loading, because grub boot order is definitely changed when a kernel upgrade happens in OS2.

It's possible to chainload one Linux with Grub to another LInux with Grub but that is not likely.  You can see this by looking at the /boot/grub/grub.cfg file.  There will be entries for each OS and the linux line generally points to a specific drive partition by UUID pointing to the kernel (vmlinuz file).

I notice that you have been trying to use boot repair.  If you have it, you could get more specific answers if you posted the specific information from boot repair by using the Create BootInfo Summary option.  
As explained above, you can have only one primary OS booting with either Legacy or UEFI and chainloading from one to a second will show a second boot menu but not change them.  The only way to answer specifically what your situation is is to post the boot repair output.

---

### Post by Dennis N on 2018-11-26
If a new version of grub packages is installed, then the UEFI boot order can be changed when that's done. But running update-grub does not install new grub packages - the 'grub' in 'update-grub' refers to the grub menu you get when you boot up. It creates an updated one for you. Kernel upgrades automatically run update-grub to get the new kernel into your grub menu, but these don't alter the UEFI boot order. 

Could be the grub packages were upgraded (requiring an install) during some update session. Kernel could also be upgraded in same session. Result is change in UEFI boot order - caused by the first of these upgrades and not the second.

In Ubuntu, grub-install commands used when installing new grub version include adding a UEFI boot menu entry in the first position. I've noticed that some other distros do not alter the UEFI boot order when updating already installed grub packages - I think Fedora is one, but I'm not positive that's where I noticed this.

---

### Post by aeronutt on 2018-11-26
Thanks for the help!
Below is output from boot-repair info. Note that this was run from "OS2", after "apt full-upgrade"  was run on "OS2" and changed the grub boot menu:

```
 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   937,703,087   937,703,087  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048   937,701,375   937,699,328 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/mapper/veracrypt1 8a620a1b-9b0d-4b80-90c7-921f3f5ef3c7   ext4       
/dev/nvme0n1                                                       
/dev/nvme0n1p1   2E2C-9EC7                              vfat       
/dev/nvme0n1p2   6d79751a-7fc8-434a-9b1d-0d950702701a   ext4       
/dev/nvme0n1p3   fe534b87-bdf3-4464-8f4f-53e4ab624e83   ext4       
/dev/nvme0n1p4   05b64b20-9d85-4de8-ad91-f9812e40f03c   ext4       
/dev/nvme0n1p5   9d360e83-b90e-4c31-ae50-027a9e6380f8   ext4       
/dev/nvme0n1p6   98c33a0c-cd93-4ced-bb90-a2b84275a2b5   ext4       mybootfiles
/dev/sda1                                                          

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Nov 26 16:09 ata-SATA_SSD_18050248000904 -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 26 16:09 ata-SATA_SSD_18050248000904-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 26 16:09 dm-name-veracrypt1 -> ../../dm-0
lrwxrwxrwx 1 root root 13 Nov 26 16:09 nvme-PCIe_SSD_18042312800187 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-PCIe_SSD_18042312800187-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-PCIe_SSD_18042312800187-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-PCIe_SSD_18042312800187-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-PCIe_SSD_18042312800187-part4 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-PCIe_SSD_18042312800187-part5 -> ../../nvme0n1p5
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-PCIe_SSD_18042312800187-part6 -> ../../nvme0n1p6
lrwxrwxrwx 1 root root 13 Nov 26 16:09 nvme-eui.6479a707000300bb -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-eui.6479a707000300bb-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-eui.6479a707000300bb-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-eui.6479a707000300bb-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-eui.6479a707000300bb-part4 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-eui.6479a707000300bb-part5 -> ../../nvme0n1p5
lrwxrwxrwx 1 root root 15 Nov 26 16:09 nvme-eui.6479a707000300bb-part6 -> ../../nvme0n1p6

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
veracrypt1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/veracrypt1 /mnt/abc-vcrypt          ext4       (rw,relatime)
/dev/nvme0n1p1   /boot/efi                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p2   /                        ext4       (rw,relatime,errors=remount-ro)
/dev/nvme0n1p6   /mnt/mybootfiles         ext4       (rw,relatime,errors=remount-ro)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  ad 11 04 76 9f 29 ab ef  8c 24 ef be 95 f0 54 2a  |...v.)...$....T*|
00000010  6e 06 8d 31 72 2e 7a 6f  98 e3 d9 e5 ab a8 f5 e0  |n..1r.zo........|
00000020  bb 2c 89 2a 3b 0f 28 a7  bd dc 27 ce 34 91 b5 74  |.,.*;.(...'.4..t|
00000030  9d f3 19 52 72 25 36 8d  0c 10 b5 12 10 27 de a3  |...Rr%6......'..|
00000040  ad 2e d4 0c 5b 52 5f f0  1c 25 ab 8b 4b 2b 7c 9e  |....[R_..%..K+|.|
00000050  07 17 d7 33 29 fa 64 61  42 81 99 c8 f3 3f 00 6c  |...3).daB....?.l|
00000060  38 48 4e f1 29 e4 bd 88  67 f3 7b 74 c9 04 13 3c  |8HN.)...g.{t...<|
00000070  46 d8 16 84 cd b5 15 8f  cf 8e 19 1e 7d 1d 3e 72  |F...........}.>r|
00000080  d4 24 54 8c 36 77 bd d3  d6 97 ef 19 1d d4 cb d6  |.$T.6w..........|
00000090  0c 88 b1 fe 49 89 d6 c8  e2 d4 f0 a7 99 b8 70 e8  |....I.........p.|
000000a0  2f bf 64 5f ca 8e 6b 5f  22 67 64 d2 ab f4 54 36  |/.d_..k_"gd...T6|
000000b0  d2 25 fd 78 27 4e 31 2e  87 c4 2c b9 14 fa 3c f0  |.%.x'N1...,...<.|
000000c0  5e b2 30 a0 19 ca 94 50  63 26 d8 4d 89 a3 b0 71  |^.0....Pc&.M...q|
000000d0  50 a7 34 aa d8 91 94 4e  a4 c6 58 ca 1a 3b 7b 02  |P.4....N..X..;{.|
000000e0  bf 37 71 cf 9c 77 ad 53  a5 e7 56 9b b5 b5 45 52  |.7q..w.S..V...ER|
000000f0  fd 20 c7 eb d6 ae d5 ed  b6 94 ac a3 da 79 b8 cc  |. ...........y..|
00000100  2d 80 ef e4 cb 83 98 19  f5 c3 a5 8b 1a e2 78 a1  |-.............x.|
00000110  2f fe 74 f0 df 91 f2 9a  67 ed 8c cd b0 15 0f 96  |/.t.....g.......|
00000120  e1 82 f3 11 05 90 04 1d  6b cd a6 70 5d 2c ca 32  |........k..p],.2|
00000130  0c 16 cc a4 31 60 5e 13  4e e0 1c 0f 58 51 e0 0b  |....1`^.N...XQ..|
00000140  b4 2b 01 a8 07 38 b0 e7  ef 7e b5 4f 09 b1 c6 fa  |.+...8...~.O....|
00000150  3a a6 8d 95 00 2a 26 6d  0c 8f 0d 41 94 b1 66 59  |:....*&m...A..fY|
00000160  d3 1b 05 71 10 67 24 b8  12 d8 5d 4b 87 9a b6 2c  |...q.g$...]K...,|
00000170  6a b7 5c de f5 39 1d 68  9f 6d 55 4f 33 74 7f d7  |j.\..9.h.mUO3t..|
00000180  d6 7f 81 90 ea 41 c2 04  67 50 58 42 a7 28 30 72  |.....A..gPXB.(0r|
00000190  33 33 76 6c e3 e8 1b 57  3d 1f e8 db 82 a6 84 f2  |33vl...W=.......|
000001a0  76 fd 5e f1 0b 20 51 f9  5a 17 2d ba 71 a6 56 ce  |v.^.. Q.Z.-.q.V.|
000001b0  29 e7 b6 38 33 e8 b5 ab  0b 70 9c 2f 2d 89 0f bf  |)..83....p./-...|
000001c0  b3 07 b8 01 22 e1 83 17  99 d4 9a e3 23 fc 8e 0b  |....".......#...|
000001d0  30 75 6b a6 f8 73 8c 90  a9 90 14 2d be 8c 63 65  |0uk..s.....-..ce|
000001e0  f3 fe 16 81 ce 6d e4 9d  65 5b 10 71 a0 58 77 00  |.....m..e[.q.Xw.|
000001f0  bd 82 36 50 32 55 ca 61  6f 90 5e eb 3d 6c d8 72  |..6P2U.ao.^.=l.r|
00000200



ADDITIONAL INFORMATION :
=================== log of boot-repair 20181126_1609 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
Is there RAID on this computer? no
boot-repair is executed in installed-session (Ubuntu 18.10, cosmic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.18.0-11-generic root=UUID=6d79751a-7fc8-434a-9b1d-0d950702701a ro quiet splash
Set sda as corresponding disk of mapper/veracrypt1
Set sda as corresponding disk of mapper/veracrypt1
mount: /mnt/boot-sav/sda1: /dev/sda1 already mounted or mount point busy.
mount /dev/sda1 : Error code 32
mount -r /dev/sda1 /mnt/boot-sav/sda1
mount: /mnt/boot-sav/sda1: /dev/sda1 already mounted or mount point busy.
mount -r /dev/sda1 : Error code 32

=================== os-prober:
/dev/nvme0n1p2:The OS now in use - Ubuntu 18.10 CurrentSession:linux
/dev/nvme0n1p3:Ubuntu 18.10 (18.10):Ubuntu:linux
/dev/nvme0n1p4:Ubuntu 18.04.1 LTS (18.04):Ubuntu1:linux
/dev/nvme0n1p5:Ubuntu 18.10 (18.10):Ubuntu2:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/nvme0n1p1: UUID="2E2C-9EC7" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="3383731c-e7e8-43e1-b9db-4df2bc056bfe"
/dev/nvme0n1p2: UUID="6d79751a-7fc8-434a-9b1d-0d950702701a" TYPE="ext4" PARTUUID="7532593a-df43-49b6-a054-7f383b8e6d33"
/dev/nvme0n1p3: UUID="fe534b87-bdf3-4464-8f4f-53e4ab624e83" TYPE="ext4" PARTUUID="c477cb8e-47d0-45e5-94f7-0fd589275608"
/dev/nvme0n1p4: UUID="05b64b20-9d85-4de8-ad91-f9812e40f03c" TYPE="ext4" PARTUUID="605b6fe1-81fa-4441-a77c-bf4e74e3dc39"
/dev/nvme0n1p5: UUID="9d360e83-b90e-4c31-ae50-027a9e6380f8" TYPE="ext4" PARTUUID="367a66a2-4631-4361-aa5c-e2e7883af19f"
/dev/nvme0n1p6: LABEL="mybootfiles" UUID="98c33a0c-cd93-4ced-bb90-a2b84275a2b5" TYPE="ext4" PARTLABEL="mybootfiles" PARTUUID="c871470b-74cf-4222-b43b-f2213d5bb038"
/dev/mapper/veracrypt1: UUID="8a620a1b-9b0d-4b80-90c7-921f3f5ef3c7" TYPE="ext4"
/dev/nvme0n1: PTUUID="46bb5e91-637a-4707-afc4-852984da9995" PTTYPE="gpt"
/dev/sda1: PARTLABEL="abc-vcrypt" PARTUUID="4f8752f8-69af-4ff4-92ba-fc162a0cc212"


1 disks with OS, 4 OS : 4 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

mount: /mnt/boot-sav/sda1: /dev/sda1 already mounted or mount point busy.
mount /dev/sda1 : Error code 32
mount -r /dev/sda1 /mnt/boot-sav/sda1
mount: /mnt/boot-sav/sda1: /dev/sda1 already mounted or mount point busy.
mount -r /dev/sda1 : Error code 32

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Nov  9 22:11 grub.d
total 84
-rwxr-xr-x 1 root root 10364 Oct 17 14:44 00_header
-rwxr-xr-x 1 root root  6258 Oct 17 14:41 05_debian_theme
-rwxr-xr-x 1 root root 13716 Oct 17 14:44 10_linux
-rwxr-xr-x 1 root root 11495 Oct 17 14:44 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rw-r--r-- 1 root root  1885 Nov  9 22:11 25_custom
-rwxr-xr-x 1 root root 12059 Oct 17 14:44 30_os-prober
-rwxr-xr-x 1 root root  1418 Oct 17 14:44 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 17 14:44 40_custom
-rwxr-xr-x 1 root root   216 Oct 17 14:44 41_custom
-rw-r--r-- 1 root root   483 Oct 17 14:44 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of nvme0n1p2: UUID=2E2C-9EC7	 (nvme0n1p1)
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/fallback.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/fbia32.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/fbx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/mmx64.efi
Presence of bkp file detected: /boot/efi/EFI/BOOT/bkpbootx64.efi

=================== nvme0n1p3/etc/grub.d/ :
drwxr-xr-x  2 root   root     4096 Oct 17 18:38 grub.d
total 80
-rwxr-xr-x 1 root root 10364 Oct 17 14:44 00_header
-rwxr-xr-x 1 root root  6258 Oct 17 14:41 05_debian_theme
-rwxr-xr-x 1 root root 13716 Oct 17 14:44 10_linux
-rwxr-xr-x 1 root root 11495 Oct 17 14:44 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 12059 Oct 17 14:44 30_os-prober
-rwxr-xr-x 1 root root  1418 Oct 17 14:44 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 17 14:44 40_custom
-rwxr-xr-x 1 root root   216 Oct 17 14:44 41_custom
-rw-r--r-- 1 root root   483 Oct 17 14:44 README




=================== nvme0n1p3/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of nvme0n1p3: UUID=2E2C-9EC7   (nvme0n1p1)

=================== nvme0n1p4/etc/grub.d/ :
drwxr-xr-x  2 root root        4096 Nov 25 12:40 grub.d
drwxr-xr-x  2 root root        4096 Jun  8 14:02 grub.d.bak
total 80
-rwxr-xr-x 1 root root  9783 Mar  4  2018 00_header
-rwxr-xr-x 1 root root  6258 Mar  4  2018 05_debian_theme
-rwxr-xr-x 1 root root 12693 Mar  4  2018 10_linux
-rwxr-xr-x 1 root root 11298 Mar  4  2018 20_linux_xen
-rwxr-xr-x 1 root root 12059 Mar  4  2018 30_os-prober
-rwxr-xr-x 1 root root  1418 Mar  4  2018 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Mar  4  2018 40_custom
-rwxr-xr-x 1 root root   216 Mar  4  2018 41_custom
-rw-r--r-- 1 root root  1621 Aug 10 08:33 hold.25_custom.hold
-rw-r--r-- 1 root root   483 Mar  4  2018 README




=================== nvme0n1p4/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of nvme0n1p4: UUID=2E2C-9EC7	 (nvme0n1p1)

=================== nvme0n1p5/etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Oct 17 18:31 grub.d
total 80
-rwxr-xr-x 1 root root 10364 Oct 17 14:44 00_header
-rwxr-xr-x 1 root root  6258 Oct 17 14:41 05_debian_theme
-rwxr-xr-x 1 root root 13716 Oct 17 14:44 10_linux
-rwxr-xr-x 1 root root 11495 Oct 17 14:44 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 12059 Oct 17 14:44 30_os-prober
-rwxr-xr-x 1 root root  1418 Oct 17 14:44 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 17 14:44 40_custom
-rwxr-xr-x 1 root root   216 Oct 17 14:44 41_custom
-rw-r--r-- 1 root root   483 Oct 17 14:44 README




=================== nvme0n1p5/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=2
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of nvme0n1p5: UUID=2E2C-9EC7   (nvme0n1p1)
/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0008
Boot0000* ubuntu	HD(1,GPT,3383731c-e7e8-43e1-b9db-4df2bc056bfe,0x800,0x100000)/File(EFIubuntugrubx64.efi)
Boot0008* UEFI: PCIe SSD, Partition 1	HD(1,GPT,3383731c-e7e8-43e1-b9db-4df2bc056bfe,0x800,0x100000)/File(EFIbootbootx64.efi)..BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
nvme0n1p2	: nvme0n1,	not-sepboot,	grubenv-ok	grub2,	signed grub-pc grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	notbiosboot, .
nvme0n1p1	: nvme0n1,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	notbiosboot, /boot/efi.
nvme0n1p3	: nvme0n1,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	notbiosboot, /mnt/boot-sav/nvme0n1p3.
nvme0n1p4	: nvme0n1,	not-sepboot,	grubenv-ok	grub2,	grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	notbiosboot, /mnt/boot-sav/nvme0n1p4.
nvme0n1p5	: nvme0n1,	not-sepboot,	grubenv-ok	grub2,	signed grub-pc grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/nvme0n1p5.
nvme0n1p6	: nvme0n1,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/mybootfiles.
mapper/veracrypt1	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/abc-vcrypt.
sda1	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/sda1.

nvme0n1	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes
sda	: GPT,	no-BIOS_boot,	has-no-EFIpart, 	not-usb,	not-mmc, no-os,	2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:480GB:scsi:512:512:gpt:ATA SATA SSD:;
1:1049kB:480GB:480GB::abc-vcrypt:;

BYT;
/dev/mapper/veracrypt1:480GB:dm:512:512:loop:Linux device-mapper (crypt):;
1:0.00B:480GB:480GB:ext4::;

BYT;
/dev/nvme0n1:128GB:nvme:512:512:gpt:PCIe SSD:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:32.0GB:31.5GB:ext4::;
3:32.0GB:63.5GB:31.5GB:ext4::;
4:63.5GB:94.9GB:31.5GB:ext4::;
5:94.9GB:124GB:28.9GB:ext4::;
6:124GB:128GB:4194MB:ext4:mybootfiles:;

=================== lsblk:
KNAME     TYPE FSTYPE     SIZE LABEL
loop0     loop squashfs 140.7M
loop1     loop squashfs  87.9M
loop2     loop squashfs 140.9M
sda       disk          447.1G
sda1      part          447.1G
dm-0      dm   ext4     447.1G
nvme0n1   disk          119.2G
nvme0n1p1 part vfat       512M
nvme0n1p2 part ext4      29.3G
nvme0n1p3 part ext4      29.3G
nvme0n1p4 part ext4      29.3G
nvme0n1p5 part ext4        27G
nvme0n1p6 part ext4       3.9G mybootfiles

KNAME     ROTA RO RM STATE   MOUNTPOINT
loop0        1  1  0         /snap/gnome-3-26-1604/74
loop1        1  1  0         /snap/core/5662
loop2        1  1  0         /snap/gnome-3-26-1604/70
sda          0  0  0 running
sda1         0  0  0
dm-0         0  0  0 running /mnt/abc-vcrypt
nvme0n1      0  0  0 live
nvme0n1p1    0  0  0         /boot/efi
nvme0n1p2    0  0  0         /
nvme0n1p3    0  0  0         /mnt/boot-sav/nvme0n1p3
nvme0n1p4    0  0  0         /mnt/boot-sav/nvme0n1p4
nvme0n1p5    0  0  0         /mnt/boot-sav/nvme0n1p5
nvme0n1p6    0  0  0         /mnt/mybootfiles


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3983872k,nr_inodes=995968,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=801272k,mode=755)
/dev/nvme0n1p2 on / type ext4 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
bpf on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=29,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14704)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/var/lib/snapd/snaps/gnome-3-26-1604_74.snap on /snap/gnome-3-26-1604/74 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_5662.snap on /snap/core/5662 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_70.snap on /snap/gnome-3-26-1604/70 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/nvme0n1p6 on /mnt/mybootfiles type ext4 (rw,relatime,errors=remount-ro)
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=801268k,mode=700,uid=1000,gid=1000)
veracrypt on /tmp/.veracrypt_aux_mnt1 type fuse.veracrypt (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)
/dev/mapper/veracrypt1 on /mnt/abc-vcrypt type ext4 (rw,relatime)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/nvme0n1p3 on /mnt/boot-sav/nvme0n1p3 type ext4 (rw,relatime)
/dev/nvme0n1p4 on /mnt/boot-sav/nvme0n1p4 type ext4 (rw,relatime)
/dev/nvme0n1p5 on /mnt/boot-sav/nvme0n1p5 type ext4 (rw,relatime)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/nvme0n1 (filtered):  alignment_offset bdi capability dev device discard_alignment eui ext_range hidden holders inflight integrity mq nsid nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 nvme0n1p5 nvme0n1p6 power queue range removable ro size slaves stat subsystem trace uevent wwid
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 size slaves stat subsystem trace uevent
/dev (filtered):  acpi_thermal_rel autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dm-0 dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 ecryptfs fb0 fd freefall full fuse hidraw0 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 initctl input kmsg kvm lightnvm log mapper mcelog mei0 mem memory_bandwidth mqueue net network_latency network_throughput null nvme0 nvme0n1 nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 nvme0n1p5 nvme0n1p6 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sg0 shm snapshot snd stderr stdin stdout uhid uinput urandom userio vboxdrv vboxdrvu vboxnetctl vfio vga_arbiter vhci vhost-net vhost-vsock wmi zero
ls /dev/mapper:  control veracrypt1

=================== hexdump -n512 -C /dev/nvme0n1p1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  20 00 40 00 00 08 00 00  |........ .@.....|
00000020  00 00 10 00 00 04 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 c7 9e 2c 2e 4e  4f 20 4e 41 4d 45 20 20  |..)..,.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem             Type      Size  Used Avail Use% Mounted on
udev                   devtmpfs  3.8G     0  3.8G   0% /dev
tmpfs                  tmpfs     783M  1.8M  781M   1% /run
/dev/nvme0n1p2         ext4       29G  9.6G   18G  36% /
tmpfs                  tmpfs     3.9G   50M  3.8G   2% /dev/shm
tmpfs                  tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                  tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0             squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop1             squashfs   88M   88M     0 100% /snap/core/5662
/dev/loop2             squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/nvme0n1p6         ext4      3.8G  148M  3.5G   5% /mnt/mybootfiles
/dev/nvme0n1p1         vfat      511M   30M  482M   6% /boot/efi
tmpfs                  tmpfs     783M  7.1M  776M   1% /run/user/1000
/dev/mapper/veracrypt1 ext4      440G  153G  265G  37% /mnt/abc-vcrypt
/dev/nvme0n1p3         ext4       29G  9.2G   19G  34% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4         ext4       29G   11G   17G  40% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5         ext4       27G  8.2G   17G  33% /mnt/boot-sav/nvme0n1p5

=================== fdisk -l:
Disk /dev/loop0: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 87.9 MiB, 92123136 bytes, 179928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 46BB5E91-637A-4707-AFC4-852984DA9995

Device             Start       End  Sectors  Size Type
/dev/nvme0n1p1      2048   1050623  1048576  512M EFI System
/dev/nvme0n1p2   1050624  62490077 61439454 29.3G Linux filesystem
/dev/nvme0n1p3  62490624 123930077 61439454 29.3G Linux filesystem
/dev/nvme0n1p4 123930624 185370077 61439454 29.3G Linux filesystem
/dev/nvme0n1p5 185370624 241876483 56505860   27G Linux filesystem
/dev/nvme0n1p6 241876992 250068991  8192000  3.9G Linux filesystem


Disk /dev/sda: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0FEDBE15-F2E6-4793-ADC9-62ECEE75F8B1

Device     Start       End   Sectors   Size Type
/dev/sda1   2048 937701375 937699328 447.1G Linux filesystem


Disk /dev/mapper/veracrypt1: 447.1 GiB, 480101793792 bytes, 937698816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of nvme0n1p2, using the following options:        nvme0n1p1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file  restore-efi-backups


=================== Advice in case of suggested repair
You may want to retry after decrypting your partitions. (https://help.ubuntu.com/community/EncryptedPrivateDirectory)
Do you want to continue?


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on nvme0n1p1/efi/.../grub*.efi file!


=================== User settings
The settings chosen by the user will not act on the boot.




```

---

### Post by oldfred on 2018-11-26
Better to attach link to summary report.

But report not updated for NVMe drives, so missing some data. But some other data also seems to be missing.
I just ran new copy of my report, I have multiple installs, but drives are sda, sdb, etc.
[http://paste.ubuntu.com/p/hsXNWGJxcX/](http://paste.ubuntu.com/p/hsXNWGJxcX/)
       This paste expires on 2018-12-27. 

Post these, that is elel or lower case L:
ll /boot/efi/EFI
ll /boot/efi/EFI/BOOT
ll /boot/efi/EFI/ubuntu
cat /boot/efi/EFI/ubuntu/grub.cfg

---

### Post by aeronutt on 2018-11-26
Here you go:
[https://paste.ubuntu.com/p/SzmTxkmjdf/](https://paste.ubuntu.com/p/SzmTxkmjdf/)

---

### Post by oldfred on 2018-11-26
From your grub.cfg in the ESP.

      ```
 search.fs_uuid [COLOR=#ff0000]6d79751a-7fc8-434a-9b1d-0d950702701a [/COLOR]root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg 


```

And Boot-Repairs listing of blkid or lsblk shows that UUID is your second partition.
```
 /dev/nvme0n1p2   6d79751a-7fc8-434a-9b1d-0d950702701a   ext4   


```
So your default boot is the install on /dev/nvme0n1p2.

I often have to edit the first line in the grub.cfg in my ESP as second installs overwrite it. But I have backed up my ESP, used to restore old /EFI/ubuntu, but now find it just quicker to edit UUID & drive partition info.

---

### Post by aeronutt on 2018-11-27
Yes, and that is what my grub menu shows at boot.
However, my question is, why did this change from /dev/nvme0n1p3 to /dev/nvme0n1p2 after running "sudo apt full-upgrade" on /dev/nvme0n1p2?

**HANG ON, something is screwed up. Will update.**

**UPDATE, ignore my statement above**. 
/dev/nvme0n1p2 is NOT shown as my primary.
/dev/nvme0n1p4 is  shown as my primary, which is the OS that most recently installed a new kernel via "sudo apt full-upgrade".

[https://i.imgur.com/eeR9CH7.jpg](https://i.imgur.com/eeR9CH7.jpg)

---

### Post by oldfred on 2018-11-27
Default boot line, first line does not tell what it is.
I usually changed description in grub. The example from my notes are old, but it still is the same.
With UEFI it does cause some things to watch. It also uses that description for UEFI entry. But then somewhere in Ubuntu's grub, it is hard coded to "ubuntu", so you have to have both /EFI/ubuntu and /EFI/new_name. It may not create the /EFI/ubuntu folder which you will have to have. The # converts original entry to comment, so easy to change back.


```
 sudo nano -B /etc/default/grub
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="Xubuntu-12.04-amd64 Precise"
sudo update-grub 


```

---

### Post by aeronutt on 2018-11-27
Thanks, I had wondered how to relabel those, but that's not my real problem.  
As I'm figuring out how grub works, I get more confused. So, here's where I'm confused.
As I understand it:
- The parition UUID shown in /boot/efi/EFI/ubuntu/grub.cfg file should be the same partition that is first in the list of the grub menu shown when booting.

Here are a few pics of everything as is occurs now. I booted the top most default OS partition.
HOWEVER, **note that the UUID of the booted partition does NOT match the UUID of the partition in grub.cfg**.

[https://i.imgur.com/eeR9CH7.jpg](https://i.imgur.com/eeR9CH7.jpg)

[https://i.imgur.com/Ruqw7Zm.jpg](https://i.imgur.com/Ruqw7Zm.jpg)

Hence, my confusion.

---

### Post by oldfred on 2018-11-27
Did you change boot order in grub menu of default?
Or choose something other than first line/default in grub menu.

Post this:
lsblk -f

---

### Post by aeronutt on 2018-11-27
> **oldfred said:**
> Did you change boot order in grub menu of default?
Or choose something other than first line/default in grub menu.

No, no.


> **oldfred said:**
> 
Post this:
lsblk -f

[~] $ lsblk -f
NAME           FSTYPE   LABEL       UUID                                 MOUNTPOINT
loop0          squashfs                                                  /snap/core/5662
loop1          squashfs                                                  /snap/core/5897
loop2          squashfs                                                  /snap/core/5742
sda                                                                      
&#9492;&#9472;sda1                                                                   
  &#9492;&#9472;veracrypt1 ext4                 8a620a1b-9b0d-4b80-90c7-921f3f5ef3c7 /mnt/abc-vcrypt
nvme0n1                                                                  
&#9500;&#9472;nvme0n1p1    vfat                 2E2C-9EC7                            /boot/efi
&#9500;&#9472;nvme0n1p2    ext4                 6d79751a-7fc8-434a-9b1d-0d950702701a 
&#9500;&#9472;nvme0n1p3    ext4                 fe534b87-bdf3-4464-8f4f-53e4ab624e83 
&#9500;&#9472;nvme0n1p4    ext4                 05b64b20-9d85-4de8-ad91-f9812e40f03c /
&#9500;&#9472;nvme0n1p5    ext4                 9d360e83-b90e-4c31-ae50-027a9e6380f8 
&#9492;&#9472;nvme0n1p6    ext4     mybootfiles 98c33a0c-cd93-4ced-bb90-a2b84275a2b5 /mnt/mybootfiles

---

### Post by oldfred on 2018-11-27
Did you install into p4 after posting the /boot/efi/EFI/ubuntu/grub.cfg?

Post this again:
cat /boot/efi/EFI/ubuntu/grub.cfg 				
Post grub.cfg from p2 & p4.
You will have to mount p2, if you click on it in Naulitus it will automount. But I label partitions so I know which is which, so when not in fstab with a name/label I know, the automount uses a good label.
cat /boot/grub/grub.cfg
where ever your mount is:
cat /media/$USER/"probably some long UUID"/boot/grub/grub.cfg

I typically label to gparted when I create partitions, but if reformatting during install it gets erased. I then usually use Disks, sometimes gparted or command line to add labels.
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labeling_the_partitions](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labeling_the_partitions)

I have so many installs/partitions, I have to label to keep track.

```
fred@bionic-z97:~$ lsblk -f
NAME    FSTYPE LABEL     UUID                                 MOUNTPOINT
sda                                                           
&#9500;&#9472;sda1  vfat             F626-A4D4                            /boot/efi
&#9500;&#9472;sda2                                                        
&#9500;&#9472;sda3  ext4   trusty    45de38c8-6748-4634-b207-628d9aa8b42b 
&#9500;&#9472;sda4  swap             3af6a910-59f8-4719-b58c-2e7484d435f0 
&#9500;&#9472;sda5  ext4   iso_ssd   695d18b5-16f8-4e9c-bf66-675a12da5a26 
&#9500;&#9472;sda6  ext4   xenial    255a2800-b871-4fdf-a809-16987e64b8b3 
&#9492;&#9472;sda7  ext4   bionic    8c92557f-cc60-438b-b1ea-ffea0adf0a1a /
sdb                                                           
&#9500;&#9472;sdb1  vfat   ESP_B     68CD-3368                            
&#9500;&#9472;sdb2                                                        
&#9500;&#9472;sdb3  ext4             76dc1759-fff1-419e-85a8-978b35537b0b 
&#9500;&#9472;sdb4  ext4   data      a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data
&#9500;&#9472;sdb5  ext4   backup    084de40f-8ffd-4af1-97b1-8a60cdd9aab4 
&#9500;&#9472;sdb6  ext4   iso_hdd   7f360ddc-d9fb-4a40-b17a-f2d5af6b61ed 
&#9500;&#9472;sdb7  swap             a7750d57-5381-421b-82fa-b53194ab45c2 [SWAP]
&#9500;&#9472;sdb8  ext4   debian    cf713b4c-6d8d-4289-b152-fc54051213e8 
&#9500;&#9472;sdb10 ext4   bionicb   819db222-6f4f-42d5-8b20-491bdc09693c 
&#9500;&#9472;sdb11 ntfs             1C63ADBD4E4DE923                     
&#9492;&#9472;sdb12 ext4   cosmic_b  6ee4e5b7-cd2f-43f7-bf48-508980d29277 
sdc                                                           
&#9500;&#9472;sdc1  vfat   ESP_C     A124-26A6                            
&#9500;&#9472;sdc2                                                        
&#9500;&#9472;sdc3  ext4   rootc     f0740999-017f-4a68-9f97-6af9960f497c 
&#9500;&#9472;sdc4  ext4   backup_c  e03e432e-6b3a-40e7-92dc-ffda559c4693 
&#9492;&#9472;sdc5  ext4   old_data  cffe5249-4cac-4f99-8271-186d48464d3e 
sdd                                                           
&#9500;&#9472;sdd1  vfat   ESP       98F7-4FF3                            
&#9500;&#9472;sdd2                                                        
&#9500;&#9472;sdd3  ext4   bionicUSB 46b3d09b-3dfe-4325-86e8-4c8c644d8944 /media/fred/bionic
&#9492;&#9472;sdd4  ext4   data      fe02cdc0-b5bf-4278-aa55-4a1bce6d39b9 /media/fred/data

```

---

### Post by aeronutt on 2018-11-27
Again, thanks for the help!
No installs, and no kernel updates that I know of, since I posted any of this info.
Again, the odd thing is, an install did NOT cause this oddity, a kernel update via "sudo apt full-upgrade" did.

Here we go:

From p2 (current booted partition):
```
[~] $ cat /boot/efi/EFI/ubuntu/grub.cfg 
search.fs_uuid 6d79751a-7fc8-434a-9b1d-0d950702701a root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

From p4:
```
[~] $ cat /media/abc/05b64b20-9d85-4de8-ad91-f9812e40f03c/boot/grub/grub.cfg 
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  05b64b20-9d85-4de8-ad91-f9812e40f03c
else
  search --no-floppy --fs-uuid --set=root 05b64b20-9d85-4de8-ad91-f9812e40f03c
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=1
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-05b64b20-9d85-4de8-ad91-f9812e40f03c' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root  05b64b20-9d85-4de8-ad91-f9812e40f03c
	else
	  search --no-floppy --fs-uuid --set=root 05b64b20-9d85-4de8-ad91-f9812e40f03c
	fi
        linux	/boot/vmlinuz-4.15.0-39-generic root=UUID=05b64b20-9d85-4de8-ad91-f9812e40f03c ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.15.0-39-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-05b64b20-9d85-4de8-ad91-f9812e40f03c' {
	menuentry 'Ubuntu, with Linux 4.15.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-39-generic-advanced-05b64b20-9d85-4de8-ad91-f9812e40f03c' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  05b64b20-9d85-4de8-ad91-f9812e40f03c
		else
		  search --no-floppy --fs-uuid --set=root 05b64b20-9d85-4de8-ad91-f9812e40f03c
		fi
		echo	'Loading Linux 4.15.0-39-generic ...'
	        linux	/boot/vmlinuz-4.15.0-39-generic root=UUID=05b64b20-9d85-4de8-ad91-f9812e40f03c ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-39-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-39-generic-recovery-05b64b20-9d85-4de8-ad91-f9812e40f03c' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  05b64b20-9d85-4de8-ad91-f9812e40f03c
		else
		  search --no-floppy --fs-uuid --set=root 05b64b20-9d85-4de8-ad91-f9812e40f03c
		fi
		echo	'Loading Linux 4.15.0-39-generic ...'
	        linux	/boot/vmlinuz-4.15.0-39-generic root=UUID=05b64b20-9d85-4de8-ad91-f9812e40f03c ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-39-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-38-generic-advanced-05b64b20-9d85-4de8-ad91-f9812e40f03c' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  05b64b20-9d85-4de8-ad91-f9812e40f03c
		else
		  search --no-floppy --fs-uuid --set=root 05b64b20-9d85-4de8-ad91-f9812e40f03c
		fi
		echo	'Loading Linux 4.15.0-38-generic ...'
	        linux	/boot/vmlinuz-4.15.0-38-generic root=UUID=05b64b20-9d85-4de8-ad91-f9812e40f03c ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-38-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-38-generic-recovery-05b64b20-9d85-4de8-ad91-f9812e40f03c' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  05b64b20-9d85-4de8-ad91-f9812e40f03c
		else
		  search --no-floppy --fs-uuid --set=root 05b64b20-9d85-4de8-ad91-f9812e40f03c
		fi
		echo	'Loading Linux 4.15.0-38-generic ...'
	        linux	/boot/vmlinuz-4.15.0-38-generic root=UUID=05b64b20-9d85-4de8-ad91-f9812e40f03c ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-38-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p2)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-6d79751a-7fc8-434a-9b1d-0d950702701a' {
	insmod part_gpt
	insmod ext2
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root  6d79751a-7fc8-434a-9b1d-0d950702701a
	else
	  search --no-floppy --fs-uuid --set=root 6d79751a-7fc8-434a-9b1d-0d950702701a
	fi
	linux /boot/vmlinuz-4.18.0-11-generic root=UUID=6d79751a-7fc8-434a-9b1d-0d950702701a ro quiet splash $vt_handoff
	initrd /boot/initrd.img-4.18.0-11-generic
}
submenu 'Advanced options for Ubuntu 18.10 (18.10) (on /dev/nvme0n1p2)' $menuentry_id_option 'osprober-gnulinux-advanced-6d79751a-7fc8-434a-9b1d-0d950702701a' {
	menuentry 'Ubuntu (on /dev/nvme0n1p2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-11-generic--6d79751a-7fc8-434a-9b1d-0d950702701a' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  6d79751a-7fc8-434a-9b1d-0d950702701a
		else
		  search --no-floppy --fs-uuid --set=root 6d79751a-7fc8-434a-9b1d-0d950702701a
		fi
		linux /boot/vmlinuz-4.18.0-11-generic root=UUID=6d79751a-7fc8-434a-9b1d-0d950702701a ro quiet splash $vt_handoff
		initrd /boot/initrd.img-4.18.0-11-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-11-generic (on /dev/nvme0n1p2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-11-generic--6d79751a-7fc8-434a-9b1d-0d950702701a' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  6d79751a-7fc8-434a-9b1d-0d950702701a
		else
		  search --no-floppy --fs-uuid --set=root 6d79751a-7fc8-434a-9b1d-0d950702701a
		fi
		linux /boot/vmlinuz-4.18.0-11-generic root=UUID=6d79751a-7fc8-434a-9b1d-0d950702701a ro quiet splash $vt_handoff
		initrd /boot/initrd.img-4.18.0-11-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-11-generic (recovery mode) (on /dev/nvme0n1p2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-11-generic-root=UUID=6d79751a-7fc8-434a-9b1d-0d950702701a ro recovery nomodeset-6d79751a-7fc8-434a-9b1d-0d950702701a' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  6d79751a-7fc8-434a-9b1d-0d950702701a
		else
		  search --no-floppy --fs-uuid --set=root 6d79751a-7fc8-434a-9b1d-0d950702701a
		fi
		linux /boot/vmlinuz-4.18.0-11-generic root=UUID=6d79751a-7fc8-434a-9b1d-0d950702701a ro recovery nomodeset
		initrd /boot/initrd.img-4.18.0-11-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-10-generic (on /dev/nvme0n1p2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-10-generic--6d79751a-7fc8-434a-9b1d-0d950702701a' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  6d79751a-7fc8-434a-9b1d-0d950702701a
		else
		  search --no-floppy --fs-uuid --set=root 6d79751a-7fc8-434a-9b1d-0d950702701a
		fi
		linux /boot/vmlinuz-4.18.0-10-generic root=UUID=6d79751a-7fc8-434a-9b1d-0d950702701a ro quiet splash $vt_handoff
		initrd /boot/initrd.img-4.18.0-10-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-10-generic (recovery mode) (on /dev/nvme0n1p2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-10-generic-root=UUID=6d79751a-7fc8-434a-9b1d-0d950702701a ro recovery nomodeset-6d79751a-7fc8-434a-9b1d-0d950702701a' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  6d79751a-7fc8-434a-9b1d-0d950702701a
		else
		  search --no-floppy --fs-uuid --set=root 6d79751a-7fc8-434a-9b1d-0d950702701a
		fi
		linux /boot/vmlinuz-4.18.0-10-generic root=UUID=6d79751a-7fc8-434a-9b1d-0d950702701a ro recovery nomodeset
		initrd /boot/initrd.img-4.18.0-10-generic
	}
}

menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
	insmod part_gpt
	insmod ext2
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root  fe534b87-bdf3-4464-8f4f-53e4ab624e83
	else
	  search --no-floppy --fs-uuid --set=root fe534b87-bdf3-4464-8f4f-53e4ab624e83
	fi
	linux /vmlinuz root=/dev/nvme0n1p3
	initrd /initrd.img
}
submenu 'Advanced options for Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' $menuentry_id_option 'osprober-gnulinux-advanced-fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
	menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  fe534b87-bdf3-4464-8f4f-53e4ab624e83
		else
		  search --no-floppy --fs-uuid --set=root fe534b87-bdf3-4464-8f4f-53e4ab624e83
		fi
		linux /vmlinuz root=/dev/nvme0n1p3
		initrd /initrd.img
	}
	menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  fe534b87-bdf3-4464-8f4f-53e4ab624e83
		else
		  search --no-floppy --fs-uuid --set=root fe534b87-bdf3-4464-8f4f-53e4ab624e83
		fi
		linux /vmlinuz root=/dev/nvme0n1p3
		initrd /initrd.img
	}
	menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  fe534b87-bdf3-4464-8f4f-53e4ab624e83
		else
		  search --no-floppy --fs-uuid --set=root fe534b87-bdf3-4464-8f4f-53e4ab624e83
		fi
		linux /vmlinuz root=/dev/nvme0n1p3
		initrd /initrd.img.old
	}
	menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-11-generic--fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  fe534b87-bdf3-4464-8f4f-53e4ab624e83
		else
		  search --no-floppy --fs-uuid --set=root fe534b87-bdf3-4464-8f4f-53e4ab624e83
		fi
		linux /boot/vmlinuz-4.18.0-11-generic root=/dev/nvme0n1p3
		initrd /boot/initrd.img-4.18.0-11-generic
	}
	menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-10-generic--fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  fe534b87-bdf3-4464-8f4f-53e4ab624e83
		else
		  search --no-floppy --fs-uuid --set=root fe534b87-bdf3-4464-8f4f-53e4ab624e83
		fi
		linux /boot/vmlinuz-4.18.0-10-generic root=/dev/nvme0n1p3
		initrd /boot/initrd.img-4.18.0-10-generic
	}
	menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  fe534b87-bdf3-4464-8f4f-53e4ab624e83
		else
		  search --no-floppy --fs-uuid --set=root fe534b87-bdf3-4464-8f4f-53e4ab624e83
		fi
		linux /vmlinuz root=/dev/nvme0n1p3
		initrd /initrd.img
	}
	menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  fe534b87-bdf3-4464-8f4f-53e4ab624e83
		else
		  search --no-floppy --fs-uuid --set=root fe534b87-bdf3-4464-8f4f-53e4ab624e83
		fi
		linux /vmlinuz root=/dev/nvme0n1p3
		initrd /initrd.img
	}
	menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  fe534b87-bdf3-4464-8f4f-53e4ab624e83
		else
		  search --no-floppy --fs-uuid --set=root fe534b87-bdf3-4464-8f4f-53e4ab624e83
		fi
		linux /vmlinuz root=/dev/nvme0n1p3
		initrd /initrd.img.old
	}
	menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz.old--fe534b87-bdf3-4464-8f4f-53e4ab624e83' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  fe534b87-bdf3-4464-8f4f-53e4ab624e83
		else
		  search --no-floppy --fs-uuid --set=root fe534b87-bdf3-4464-8f4f-53e4ab624e83
		fi
		linux /vmlinuz.old root=/dev/nvme0n1p3
		initrd /initrd.img.old
	}
}

menuentry 'Ubuntu 18.10 (18.10) (on /dev/nvme0n1p5)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-9d360e83-b90e-4c31-ae50-027a9e6380f8' {
	insmod part_gpt
	insmod ext2
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root  9d360e83-b90e-4c31-ae50-027a9e6380f8
	else
	  search --no-floppy --fs-uuid --set=root 9d360e83-b90e-4c31-ae50-027a9e6380f8
	fi
	linux /boot/vmlinuz-4.18.0-11-generic root=UUID=9d360e83-b90e-4c31-ae50-027a9e6380f8 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-4.18.0-11-generic
}
submenu 'Advanced options for Ubuntu 18.10 (18.10) (on /dev/nvme0n1p5)' $menuentry_id_option 'osprober-gnulinux-advanced-9d360e83-b90e-4c31-ae50-027a9e6380f8' {
	menuentry 'Ubuntu (on /dev/nvme0n1p5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-11-generic--9d360e83-b90e-4c31-ae50-027a9e6380f8' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  9d360e83-b90e-4c31-ae50-027a9e6380f8
		else
		  search --no-floppy --fs-uuid --set=root 9d360e83-b90e-4c31-ae50-027a9e6380f8
		fi
		linux /boot/vmlinuz-4.18.0-11-generic root=UUID=9d360e83-b90e-4c31-ae50-027a9e6380f8 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-4.18.0-11-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-11-generic (on /dev/nvme0n1p5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-11-generic--9d360e83-b90e-4c31-ae50-027a9e6380f8' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  9d360e83-b90e-4c31-ae50-027a9e6380f8
		else
		  search --no-floppy --fs-uuid --set=root 9d360e83-b90e-4c31-ae50-027a9e6380f8
		fi
		linux /boot/vmlinuz-4.18.0-11-generic root=UUID=9d360e83-b90e-4c31-ae50-027a9e6380f8 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-4.18.0-11-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-11-generic (recovery mode) (on /dev/nvme0n1p5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-11-generic-root=UUID=9d360e83-b90e-4c31-ae50-027a9e6380f8 ro recovery nomodeset-9d360e83-b90e-4c31-ae50-027a9e6380f8' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  9d360e83-b90e-4c31-ae50-027a9e6380f8
		else
		  search --no-floppy --fs-uuid --set=root 9d360e83-b90e-4c31-ae50-027a9e6380f8
		fi
		linux /boot/vmlinuz-4.18.0-11-generic root=UUID=9d360e83-b90e-4c31-ae50-027a9e6380f8 ro recovery nomodeset
		initrd /boot/initrd.img-4.18.0-11-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-10-generic (on /dev/nvme0n1p5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-10-generic--9d360e83-b90e-4c31-ae50-027a9e6380f8' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  9d360e83-b90e-4c31-ae50-027a9e6380f8
		else
		  search --no-floppy --fs-uuid --set=root 9d360e83-b90e-4c31-ae50-027a9e6380f8
		fi
		linux /boot/vmlinuz-4.18.0-10-generic root=UUID=9d360e83-b90e-4c31-ae50-027a9e6380f8 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-4.18.0-10-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-10-generic (recovery mode) (on /dev/nvme0n1p5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.18.0-10-generic-root=UUID=9d360e83-b90e-4c31-ae50-027a9e6380f8 ro recovery nomodeset-9d360e83-b90e-4c31-ae50-027a9e6380f8' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  9d360e83-b90e-4c31-ae50-027a9e6380f8
		else
		  search --no-floppy --fs-uuid --set=root 9d360e83-b90e-4c31-ae50-027a9e6380f8
		fi
		linux /boot/vmlinuz-4.18.0-10-generic root=UUID=9d360e83-b90e-4c31-ae50-027a9e6380f8 ro recovery nomodeset
		initrd /boot/initrd.img-4.18.0-10-generic
	}
}

set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

---

### Post by oldfred on 2018-11-27
I thought the search over rode the specific partition entry. 
Yours:
search.fs_uuid 6d79751a-7fc8-434a-9b1d-0d950702701a root 
Mine:
search.fs_uuid 8c92557f-cc60-438b-b1ea-ffea0adf0a1a root hd0,gpt7 

You seem to be missing the drive, partition. Do not know if issue is NVMe drive?

This is not your boot partition as you cannot remount a mounted partition. But is your p4 partition.
cat /media/abc/05b64b20-9d85-4de8-ad91-f9812e40f03c/boot/grub/grub.cfg

---

### Post by aeronutt on 2018-11-27
> **oldfred said:**
> I thought the search over rode the specific partition entry. 
Yours:
search.fs_uuid 6d79751a-7fc8-434a-9b1d-0d950702701a root 
Mine:
search.fs_uuid 8c92557f-cc60-438b-b1ea-ffea0adf0a1a root hd0,gpt7 

You seem to be missing the drive, partition. Do not know if issue is NVMe drive?

This is not your boot partition as you cannot remount a mounted partition. But is your p4 partition.
cat /media/abc/05b64b20-9d85-4de8-ad91-f9812e40f03c/boot/grub/grub.cfg

So, you're saying that possibly, grub doesn't play well with NVMe drives?
To be clear, yes, all my OS partitions, and /boot on are my NVMe drive.

UPDATE: Maybe I'll run boot-repair in my preferred primary partition, and see what happens. Thoughts?

---

### Post by oldfred on 2018-11-27
You do not have a /boot partition. And most desktops do not need one.
You do have an ESP - efi system partition used for UEFI boot, but only one ubuntu will boot from it. 
Do not confuse them. One is ext4 and the other is FAT32.

I would see if editing your grub.efi in the ESP to have drive partition that match UUID works.

If you run Boot-Repair use advanced options and the full uninstall/reinstall of grub. That should reset everything.

---

### Post by aeronutt on 2018-11-27
Ran boot-repair. All is ok. I wish I didn't have to run boot-repair to fix issues like this, but obviously I don't understand enough to do so.  

I'm 100% confident that the next time one of the other OS's updates its kernel, I'll need to run boot-repair.  I'll try to watch for that and see if I can catch any oddity.

Anyway, again, THANKS for all the help!

---

### Post by oldfred on 2018-11-27
Glad it is working.

Save a copy of the report from boot repair.
Mine is in /var/log/boot-repair by date. Old ones you probably can delete.

---

