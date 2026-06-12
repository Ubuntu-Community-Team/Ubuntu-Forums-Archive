---
title: "Precise Install Fail (DVD media on BD-R/W sata IF)"
date: 2013-09-13
forum: Installation &amp; Upgrades
---

### Post by Brian_Brunner on 2013-09-13
I have a new rig (FX8350 on GA-990FXA-UD3).  Old rig was 64FX62 on GA-M59SLI-S5.
I have a BD-RW drive, Sata IF, in which I have a DVD of Precise Pangolin.  Winders (7) says it's "ATAPI iHBS112 2ATA device".  This device was not on the old rig.
The old rig had a pata plug, I had a pata dvd-rw.

I also have a 4GB sata drive (gpt as /dev/sda[123]), formatted as boot, swap, and root.  Winders (on /dev/sdb1) says they're ext2, although I specified ext4 when I made them.  Drives are common to  new & old rigs.

Install worked on the old rig, but fails on the new rig with a purple bar across a part of the screen, gunk that looks like text that fell into a shredder, and lots of black space between and around them. This failure occurs before any options appear with which to select anything so it's clearly the new BD-RW drive on the new MoBo being invisible to the installation kernel, or the installation kernel not working with this new Mobo).

A short while ago I installed a "ext[234] fs on Winders" sw gadget, then Winders had a crash-reboot, and the next time I booted into Precise the ext fs /dev/sda3 was badly trashed... there are more files in lost+found than out.

The "ext[234] sw gadget" (Win7 is on /dev/sdb) allows me to peer into the smoldering ruins of the old Precise install, so the drive is still OK.  The boot menu on /dev/sda1 is still good.

tl;dr join here: Are there any special parameters to get Precise to install from a SATA BD-RW device?  Onto a gpt-partitioned 4tb drive?

Thanks to all who help.  Thanks to all who try to help.  Thanks to all who just fall over laughing.  Without you three, life would be pointless and boring.

//me

---

### Post by sudodus on 2013-09-14
Welcome to the Ubuntu Forums :-)

- Did you check with *md5sum* that the download was good? And did you check that the install CD is good? (Does it work *now* in another computer)?

- You need the 64-bit version to cooperate with UEFI.

A brand new computer might contain hardware not recognized by the polished and well debugged long time support Ubuntu 12.04. Try the newest release [13.04]("http://www.ubuntu.com/download/desktop") or even the beta version of the next release [13.10]("http://iso.qa.ubuntu.com/qatracker/milestones/302/builds"). There might be drivers for your hardware in these new versions.

- What graphics card or chip is it? Can you try with the boot option nomodeset?

- Can you try booting from a USB pendrive instead of the optical drive?

---

### Post by oldfred on 2013-09-14
Sounds to me more like a video driver issue. What video card/chip do you have. Have you tried nomodeset?

With gpt drives you have to have a 1MB unformatted partition with the bios_grub flag to install in BIOS boot mode. If new motherboard it may also have UEFI, but you can still use CSM/BIOS/Legacy. But best with all systems as one or the other.

Also do not create real large / (root) partition, just because you have a large drive. Better to have a large data partition or two or /home or both.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu - Post #6 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Brian_Brunner on 2013-09-14
Thank you both Sudodus & OldFred: putting nomodeset on the /vmlinux line got me past the stop point.

---

