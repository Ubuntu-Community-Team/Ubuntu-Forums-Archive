---
title: "Major boot / Grub problems after 10.04 upgrade"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by AMWilbur on 2010-07-18
Hi folks. I know this topic has come up a few times already (I've spent most of today trying to resolve the issue myself) but I haven't found a satisfactory answer yet, and since my circumstances seem a little different I thought I'd give it a shot here. I upgraded to Ubuntu Netbook Remix 10.04 a couple days ago on my Eee PC and was loving it until I needed to get into the Windows partition. When I selected it from the Grub menu (which had been working fine), it seemed as if it was going to perform a fresh installation from a recovery disk. I can't remember quite what happened but the process was interrutped (there may have been an option to abort) because I was a bit confused about what was going on. I rebooted but instead of the Grub menu I got the Grub Rescue command line and a blinking cursor. I'm still utterly stuck as to how to access my system again.
I've followed the advice from these links:[URL="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"]
https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows[/URL]
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

and haven't managed to get very far. First, some basic info. Here's the **fdisk** readings:

> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9306    74750413+   7  HPFS/NTFS
/dev/sda2           18815       19452     5124735    c  W95 FAT32 (LBA)
/dev/sda3           19453       19457       40162+  ef  EFI (FAT-12/16/32)
/dev/sda4            9307       18814    76373010   1f  Unknown
Partition table entries are not in disk order
Disk /dev/sdc: 4026 MB, 4026531840 bytes
220 heads, 32 sectors/track, 1117 cylinders
Units = cylinders of 7040 * 512 = 3604480 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1118     3932144    b  W95 FAT32

Disk /dev/sdb: 513 MB, 513277952 bytes
9 heads, 40 sectors/track, 2784 cylinders
Units = cylinders of 360 * 512 = 184320 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2785      501131+   6  FAT16I also put **blkid** into the terminal and got this:
> /dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="7AE0A82DE0A7EE17" TYPE="ntfs"
/dev/sda2: LABEL="PE" UUID="CCED-990E" TYPE="vfat"
/dev/sdc1: LABEL="USB DISK" UUID="A6DA-8F56" TYPE="vfat"
/dev/sdb1: SEC_TYPE="msdos" LABEL="CANON_DC" UUID="64F8-1E24" TYPE="vfat"
The first time I tried the commands advised in the first link, the grub menu changed from Grub Rescue to shell mode with no menu.

I ran through the list of commands on the second link listed above and the only effect was that the** sh:** disappeared from the menu, so that the prompt just says** <Grub>**. After that installation, though, the terminal did report **Installation finished. No error reported.**

So using a Live CD I've tried a few other options but always hit a snag when some of the commands don't work. For instance, following the alternative method from the 'Reinstalling from Live CD' link, entering 
> sudo grub-setup -d/media/7AE0A82DE0A7EE17/boot/grub/dev/sdareturns **No device is specified.**
When I've tried to use the chroot method, I get caught at the first hurdle when 
> sudo mount --bind /dev /mnt/devgives me **mount: mount point /mnt/dev does not exist**

I'm pretty baffled as to how simply launching Windows could have screwed up my computer so badly. I've had to deal with relatively complicated (to a Linux neophyte) Grub issues in the past after installing new partitions, but this is really beyond me. I've also tried using the Super Grub disk Live CD but to no avail - all the various commands tend to just produce **'Error 15 - file not found'** responses.

Please help me rescue my computer! I was really impressed with the upgrade up to this point.

One last note - I'm using a netbook and I don't have an external CD drive, so the Windows MBR repair method won't work for me.

I've tried this link, too
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)
but again, after **fdisk** the commands simply don't work for me.

Thanks in advance.

---

### Post by oldfred on 2010-07-18
I assume you have a liveUSB to install in the first place. You show no Ubuntu partitions and sda4 is undefined. It may have been the extended partition. If you start the recovery it may have erased the extended partition.

I would use the liveUSB and run testdisk. I have never used it but it has recovered many missing partitions.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by AMWilbur on 2010-07-19
Hey, thanks for the advice. I've spent the last few hours working on this, using TestDisk and Gparted, and it's still getting me nowhere. 

I got testdisk working and went through all the steps outlined, each stage appearing successful to the extent that it matched what was suggested in the various documents I read. Unfortunately after rebooting it went back to the black screen with [B]grub>_    

[/B]Using GParted, I can see that my partition **sda1** is ntfs and flagged as 'boot'

**sda2 **is the other partition but is classified as an 'extended' file system, flagged as **lba **(I don't know what that means or whether it's important)

As you say, there's no sign of **sda4**

Is **sda2 **likely to be Ubuntu, with **sda1 **my Windows partition? 

At the grub prompt when I turn on the computer, I've typed in boot and it tells me that it can't find the kernel.

Do I basically need to reassign the **sda2** partition's identity as a Ubuntu system, and if so, how do I do it?

I'm very appreciative of any help and generally find this useful for understanding this aspect of computing... BUT as a devoted Ubuntu evangelist, forever boring people by telling them how great it is, I really can't believe that nobody's managed to find a way to ensure that partition installations (or simple upgrades, in this case) don't create this disaster. I'm guessing I've spent somewhere between 15 and 20 hours of my life trying to figure out how to get back into my computer after making some alteration to a partition. After all the strides that Canonical has made to make Linux accessible to a broader user base, this is exactly the kind of thing that'll put people off Linux forever.

---

### Post by oldfred on 2010-07-19
If sda2 is the extended partition then it is just a container for the logical partitions inside it. Then linux would be sda5 and swap sda6 typically. Primary partitions are sda1 thru 4 and the extended is one of the primary. Logicals start at sda5.

Did testdisk tell anything more about logical partitions. I have never used it so I do not know the details.

---

### Post by AMWilbur on 2010-07-19
Hey Oldfred, thanks for not abandoning me to an eternity of blinking cursors.

The testdisk partition structure looks like this:

> 1* HPFS-NTFS
2 E extended LBA
3 P FAT32 LBA
5 L Linux
   X extended
6 L Linux Swap
   X extended
7 L Linux Swap
   X extended
8 L Linux Swap


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted


---

### Post by AMWilbur on 2010-07-19
I have to admit that I made a mistake earlier, when I was intitially trying to fix this by reinstalling Grub 2. I mistook sda1 for my Linux partition and typed in all the commands accordingly. However, I've now tried the same process with sda3 and I'm still getting the same black grub screen, and the 'boot' command returns 'error: no loaded kernel'

---

### Post by oldfred on 2010-07-19
Your linux is in sda5 not sda3.

Run this to see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by AMWilbur on 2010-07-20
It's a miracle! I have my computer back! 

And all it took was reinstalling Grub it on sda5 (I'm searching for an embarassment emoticon...)

However, I'm a little worried about opening Windows in case this happens all over again.


Any thoughts?

Thanks for the help.

---

### Post by Bagatell on 2010-07-20
Did you get windows back? I went through a nearly identical process. Trashed the partition tables by installing grub2 to sda1 instead of sda5 but managed to restore everything with testdisk. I still can't boot windows though. When I select windows from grub it just reboots the system and dumps me back in grub. Save me from a reinstall somebody, please!

Sorted by following the bootinfoscript instructions exactly! Thanks Oldfred.

---

