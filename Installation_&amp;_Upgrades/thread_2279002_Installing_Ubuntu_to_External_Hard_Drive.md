---
title: "Installing Ubuntu to External Hard Drive"
date: 2015-05-20
forum: Installation &amp; Upgrades
---

### Post by braydenturner3 on 2015-05-20
Hello fellow Linux users, I have ran into a stump. I am currently trying to install Ubuntu 15.04 to an external hard drive via running try Ubuntu without installing off a USB stick. Yes I want it BIOS not UEFI... Also I am willing to give a reward in Bitcoins if someone can send me a step by step guide that solves my problem. Thank you for your time. Also please note that I am not a very advanced Linux user and I really don't know how to create certain size partitions in g-parted. So I do need quite specific instructions on what to do. 

Also I would love (I do not know if this is allowed) if someone could like remote control my PC and do it for me. 

The external hard drive is 3TB and I want to use the whole hard drive for Ubuntu.

---

### Post by sudodus on 2015-05-20
Welcome to the Ubuntu Forums :-)

The advice here is free, and we are volunteers, so I think you can buy something else for your bitcoins.

You want the whole drive for Ubuntu, and run in BIOS mode. That makes it rather easy, unless you want partitions to be larger than 2 GB. That is the limit for the old MSDOS partition table. But if you want your system 'future safe' and learn how to use the GUID partition table, GPT, you can follow the guide in the following links.

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

and maybe these links (more details, though made for a small pendrive)

[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506")

[https://help.ubuntu.com/community/In.../UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

-o-

You might want a separate **home** partition or a separate **data** partition.

-o-

Browse these links and after that you can start asking about details. If the target drive is clean, and you disconnect the internal drive, you can safely try to install and re-install, if something went wrong, or you get a better idea how to set up the partitions.

---

### Post by QIII on 2015-05-20
I'll be more blunt:  This is a volunteer forum.  Do not offer payment for support here.

---

### Post by braydenturner3 on 2015-05-20
> **QIII said:**
> I'll be more blunt:  This is a volunteer forum.  Do not offer payment for support here.

Sorry, I didn't know. My bad.

Edit: I removed my desktops hard drive and chose format and install ubuntu on my external hard drive and it has been on "detecting file systems" for the past hour. Should this be happening?

---

### Post by oldfred on 2015-05-20
Guys, I am planning a world tour (wife may have other opinions) and trying to get a free beer everywhere I go. :)

If over 2TB then you do have to use gpt partitioning. And if drive may be used in future on a newer UEFI system, you may want to allocate 100 to 300MB at beginning of drive even if not used now. Difficult to add efi partition later when drive has lots of data.
Also much better to have smaller / (root) partition of 25GB or so. We have seen installs where parts of grub or kernels are scattered all over very large drive, so drive has to work harder. 

I prefer to partition in advance with gparted. Not sure with large drive if it auto uses gpt or not.
 For my smaller drives I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning, first thing.

You do want to have the bios_grub partition and must select the external drive, sdb or whatever drive it is as location to install grub2 boot loader.


 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by ajgreeny on 2015-05-20
> **braydenturner3 said:**
> Sorry, I didn't know. My bad.

Edit: I removed my desktops hard drive and chose format and install ubuntu on my external hard drive and it has been on "detecting file systems" for the past hour. Should this be happening?
If your desktop has no hard drive with an OS on it, that is exactly what I would expect as it has no file-system to boot from.

I assume the external drive is attached (by USB?) but also does not have an OS or file system of any kind and that is where you want to install Ubuntu.

For the easiest way of installing, however, you do need to boot to either a DVD to which you have burned a downloaded image file, eg ubuntu-14.04-desktop-amd64.iso (that's what I used; you may want something else but they are all** .iso** files) or to a USB flash drive.  You will, however, need a computer with an OS on it in order to make a USB flash drive or burn a DVD, so unless you have another machine to use you have created a "catch 22" situation for yourself.

---

### Post by sudodus on 2015-05-20
If you have no bootable USB pendrive (with Ubuntu), you need to make one (in a computer running with an operating system). See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you have a bootable USB pendrive (with Ubuntu), you should make the computer boot from it. How to do that varies between computers, and you can usually find information about it via the internet. Sometimes it is as simple as pressing a hotkey, for example Esc or F12. Sometimes it requires that you change some setting in the UEFI/BIOS menu. The old style BIOS is often called 'CSM' in UEFI systems.

The USB pendrive with Ubuntu contains not only the installer and the separate graphical partitioner gparted, it is a whole live operating system, and you can try it (and compare it with other linux distros, that you try in a similar way, for example the Ubuntu community flavours. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

