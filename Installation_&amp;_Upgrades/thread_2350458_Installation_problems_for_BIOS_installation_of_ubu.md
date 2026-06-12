---
title: "Installation problems for BIOS installation of ubuntu 16.04"
date: 2017-01-24
forum: Installation &amp; Upgrades
---

### Post by yas1234 on 2017-01-24
Currently attempting to install ubuntu with bios settings on my machine to run along side windows. Right now I have three separate hard-drives with one already being used for the windows installation which is running in legacy mode. When I attempt to use the 16.04 bootable usb I created and go to the installation, my monitor gives an error saying not optimum mode. I have a Nvidia GTX 1060, Gigabyte motherboard with a H97 chipset and a i5 processsor. I've already tried enabling nomodeset to no avail. Is there anyway I could get to the installation phase?

---

### Post by oldfred on 2017-01-24
Most find nomodeset works.
Some have just connected to the motherboard video and installed using the Intel video. Then they install the nVidia driver using the ppa (since you need the very newest) and reconnected to the nVidia video out.

AMD Gigabyte boards have needed IOMMU settings and boot parameter setting for iommu, but did not think Intel Gigabyte boards needed that. Do you have a IOMMU setting in UEFI?

Possible similar Z97 installs. 
 Gigabyte Z170 Nvidia 970 16.04   UEFI Settings required                         
[http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04](http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04)
[https://ubuntuforums.org/showthread.php?t=2341704](https://ubuntuforums.org/showthread.php?t=2341704)
Gigabyte H170
[http://ubuntuforums.org/showthread.php?t=2312650](http://ubuntuforums.org/showthread.php?t=2312650)
Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2) 

        Asus z97-A with nVidia GTX 970 Maxwell Ubuntu  15.04
[http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896](http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896) 
            Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

Since you elected to have Windows in BIOS boot mode, that drive has to be MBR(msdos).
And with Windows in BIOS mode, better to have Ubuntu in BIOS boot mode.

But Ubuntu can boot in either UEFI or BIOS/CSM/Legacy from gpt partitioned drives, if you have correct supporting partitions.
UEFI needs the ESP & BIOS the bios_grub partition if you use gpt.
I still had XP in MBR but converted all new drives to gpt back in 2010. And in about 2012, a few years before my first UEFI system, I started adding both the bios_grub partition for my current BIOS boot, but also adding the ESP - efi system partition for future UEFI boot.

You will not be able to correctly install Ubuntu in UEFI mode as it only installs to the ESP on sda, and you do not have one. But adding ESP to your Ubuntu drive will not use much space and allow future change to UEFI.

 Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

