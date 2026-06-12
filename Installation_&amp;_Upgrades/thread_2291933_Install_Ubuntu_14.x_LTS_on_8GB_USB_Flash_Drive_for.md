---
title: "Install Ubuntu 14.x LTS on 8GB USB Flash Drive for Utilities to recover &amp; manage NAS"
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by crashnburn_in on 2015-08-24
**[Install Ubuntu 14.x LTS on 8GB USB Flash Drive for Utilities to recover & manage Synology NAS drives?]("http://askubuntu.com/questions/665076/install-ubuntu-14-x-lts-on-8gb-usb-flash-drive-for-utilities-to-recover-manage")**


[COLOR=#111111][FONT=Ubuntu]Install Ubuntu 14.x LTS on 8GB USB Flash Drive for Utilities. I am choosing LTS for long term package support.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]It is not primary usage, but goal is to use it for certain **drive recovery & management activities related to my Synology NAS**.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Having some room on it for such tools and to try some other utilities would be great.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][https://www.synology.com/en-us/knowledgebase/faq/579](https://www.synology.com/en-us/knowledgebase/faq/579)
[http://forum.synology.com/enu/viewtopic.php?t=51393](http://forum.synology.com/enu/viewtopic.php?t=51393)
[http://superuser.com/questions/550064/how-mount-find-recover-data-in-hdd-outside-of-synology-box](http://superuser.com/questions/550064/how-mount-find-recover-data-in-hdd-outside-of-synology-box)
[http://www.anandtech.com/show/8399/recovering-data-from-a-failed-synology-nas/2](http://www.anandtech.com/show/8399/recovering-data-from-a-failed-synology-nas/2)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I read about **live, persistent and full installs** on the ubuntu forums and am a bit confused on **which is the one I should choose**?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I will be using the live CD/DVD to boot up and install on this 8GB Flash Drive.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Please do advise.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**What options should I choose/ components to install or not install [given that its 8GB USB]?**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**Should I pre-partition & format using Gparted or Acronis or Paragon etc?**[/FONT][/COLOR]

---

### Post by sudodus on 2015-08-24
I think most people would use a live or persistent live system for repair and recovery purposes. Select persistence if you want to install some extra tool and/or some data files. LTS is a good option :-)

There are several tools to make USB drives bootable with Ubuntu (in other words, to install Ubuntu as a live system or a persistent live system). Some of them want a prepared USB pendrive with an MSDOS partition table and a FAT32 partition, some of them create the partition table from the beginning (overwriting all 'cruft' from previous usage of the pendrive).

Examples:

[LIST=1]
[*]***Unetbootin*** wants a prepared USB pendrive with an MSDOS partition table and a FAT32 partition.
[*]***mkusb*** creates the partition table from the beginning.
[/LIST]

See this link for more details

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

You can also install a  full Ubuntu system (like in an internal drive). If you want many extra tools and want it up to date including the kernel, this is the best alternative. In this case you should decrease the wear of the flash memory:

[LIST=1]
[*]turn off journaling (use sudo tune2fs)
[*]add the mount option noatime in /etc/fstab
[/LIST]

---

### Post by crashnburn_in on 2015-08-24
I did a default installation on it from live dvd [after going into legacy bios mode] and it installed. 

But weird thing is it quickly said drive has only 180 mb left etc. Should I avoid the default partitioning it did? [It made these: ext4: 3.55 GB | extended/linux-swap 3.82 GB ]
What kind of of partition and install do I create using GPart? 

PS: I do not wish to install From USB. I am installing from live DVD to USB Flash.

PS: I do need additional tools saved on it, so how can I do a PERSISTENT install on it? 
Due to need for additional apps/ tools that I'd have to install everytime) im not using live DVD.

Should I just install and use a Non Ubuntu distro that includes some of these tools already? 

PS: Also might want to add Kdirstat + beyond compare + ultra copier

---

### Post by sudodus on 2015-08-24
Maybe the swap partition eats a considerable part of the drive. Maybe it is enough with 256 MB or 512 MB swap. Then you can use the rest of the pendrive for the root partition. The sizes can be changed with ***gparted***.

If you have a live system (in a USB pendrive instead of in a DVD disk) with a (file named casper-rw) or partition labeled casper-rw, you have a persistent live system. It is even possible to boot such a system from DVD and have the casper-rw storage in an internal drive or USB drive.

A persistent live system can store installed programs and created or downloaded files. I works 'seamlessly', you don't notice how it is done unless you look behind the curtain. (The casper-rw file or partition is overlayed the workspace with the root partition in RAM.)

Edit: It is easier to make and better to have a casper-rw partition.

---

### Post by crashnburn_in on 2015-08-24
> **sudodus said:**
> Maybe the swap partition eats a considerable part of the drive. Maybe it is enough with 256 MB or 512 MB swap. Then you can use the rest of the pendrive for the root partition. The sizes can be changed with ***gparted***.

If you have a live system (in a USB pendrive instead of in a DVD disk) with a (file named casper-rw) or partition labeled casper-rw, you have a persistent live system. It is even possible to boot such a system from DVD and have the casper-rw storage in an internal drive or USB drive.

A persistent live system can store installed programs and created or downloaded files. I works 'seamlessly', you don't notice how it is done unless you look behind the curtain. (The casper-rw file or partition is overlayed the workspace with the root partition in RAM.)

Edit: It is easier to make and better to have a casper-rw partition.

Yes. It was taking all the space. 

After looking through these I realized I'd prefer a **Live Persistence System on the USB Flash** that _does not get attached to a system_ (drivers etc). [SIZE=2]
[/SIZE][B][SIZE=2][What would be the differences between a persistent USB Live Session and a installed Ubuntu in a USB drive?]("http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal")  
[Difference between LiveCD, LiveUSB, full-install, and persistence?]("http://askubuntu.com/questions/156026/difference-between-livecd-liveusb-full-install-and-persistence")
[/SIZE][/B]
I dont want a live cd + USB for persistence like this - [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
I'd **prefer single Live USB with persistence** -- I am guessing this - [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

This tutorial is way too long.. and verbose & confusing. 

I am guessing these installers do the same without having to do it manually? 
[http://askubuntu.com/a/52692/128859](http://askubuntu.com/a/52692/128859)

>  1) [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"):
  Universal USB Installer is a Live Linux USB Creator that allows you  to choose from a selection of Linux Distributions to put on your USB  Flash Drive. The Universal USB Installer is easy to use. Simply choose a  Live Linux Distribution, the ISO file, your Flash Drive and, Click  Install. Other features include; Persistence (if available), and the  ability to fat32 format the flash drive (recommended) to ensure a clean  install. Upon completion, you should have a ready to run bootable USB  Flash Drive with your select Linux version installed.
  2) [UNetbootin]("http://unetbootin.sourceforge.net/"):
  UNetbootin allows you to create bootable Live USB drives for Ubuntu,  Fedora, and other Linux distributions without burning a CD. It runs on  Windows, Linux, and Mac OS X. You can either let UNetbootin download one  of the many distributions supported out-of-the-box for you, or supply  your own Linux ISO file if you've already downloaded one or your  preferred distribution isn't on the list.
  3) [LinuxLive USB Creator]("http://www.linuxliveusb.com/"):
  LiLi creates portable, bootable and virtualized USB stick running  Linux.  Are you sick of having to reboot your PC to try Linux ? No need  with LiLi. It has a built-in virtualization feature that lets you run  your Linux in Windows just out of the box.
  **All three programs above allow you to install any Linux  operating system to a flash drive, but the persistence feature (allows  you to save any changes made to a LiveOS installation permanent to be  used even after reboot) is only available for Ubuntu and its many other  flavors.**  


Any pros & cons between them? 

[B]Given the following, what kind of partitioning/ space allocation should I do when I use 1/2/3 to create the PersistentLiveUSB
[/B]- I dont intend to do any major system updates (for now). I am fine with 14 LTE, just need more apps tools
- But I'd like to **maximize SPACE** _**for installing Other Software Tools and Utilities**_ and _their settings and maintain them_ (hence persistence).

---

### Post by crashnburn_in on 2015-08-24
I also went through this thread of yours - [http://ubuntuforums.org/showthread.php?t=1958073&page=15](http://ubuntuforums.org/showthread.php?t=1958073&page=15) 

Is there a page/ link with list of all such tools - with pros & cons - compared? Your preferred tools for Windows?

I am booting off Live DVD so I cant see ISO on NTFS HDD. Unless I can do it here itself I will go to Windows laptop for it.

---

### Post by oldfred on 2015-08-24
Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I have one of the older versions of Ubuntu in a 16GB flash drive with 8GB for / (root) and 8GB for data where I have other repair ISO that I can directly boot from grub. I did not add swap as system(s) I was booting would not normally use swap as they had enough RAM. I do change some settings to reduce writes.
I think it would have been better to have used one of the lighter weight flavors like Xubuntu or Lubuntu as then flash drive would not be as large & have to load as much to boot.

The only time in recent history that I have created a flash drive installer was when I had my new system and no other way to boot  in UEFI mode and install. Most of my flash drives now are larger and have full installs or just ISOs to direct boot. I was not sure how to create a direct ISO boot of UEFI grub from BIOS but now believe I could have.

---

### Post by sudodus on 2015-08-24
> **crashnburn_in said:**
> ...
Any pros & cons between them? 

[B]Given the following, what kind of partitioning/ space allocation should I do when I use 1/2/3 to create the PersistentLiveUSB
[/B]- I dont intend to do any major system updates (for now). I am fine with 14 LTE, just need more apps tools
- But I'd like to **maximize SPACE** _**for installing Other Software Tools and Utilities**_ and _their settings and maintain them_ (hence persistence).

I think all these tools work, at least for many people and in many computers. You can try more than one of them and compare the result. I have been developing ***mkusb version 10*** recently, and think it is a good alternative. It can create persistence for Ubuntu family desktop systems (32-bit as well as 64-bit systems) that run in BIOS mode as well as in UEFI mode. You can select maximum amount of available drive space for persistence, '100%'. It is not limited by the 4 GB max file size in the FAT32 file system.

[mkusb version 10](https://help.ubuntu.com/community/mkusb#mkusb_version_10)

I agree with ***oldfred*** that you should use an Ubuntu flavour with an ultra light desktop environment, Lubuntu, or Xubuntu with a medium light desktop environment. This way more drive space will be available for installing programs, and in general, it will run faster (the USB interface is slower than that of internal drives).

---

### Post by crashnburn_in on 2015-08-24
> **sudodus said:**
> If you have a live system (in a USB pendrive instead of in a DVD disk) with a (**file named casper-rw**) or **partition labeled casper-rw**, you have a **persistent live system**. It is even possible to boot such a system from DVD and have the **casper-rw storage in an internal drive or USB drive**.

A persistent live system can store installed programs and created or downloaded files. I works 'seamlessly', you don't notice how it is done unless you look behind the curtain. (The **casper-rw file or partition is overlayed** the workspace with the root partition in RAM.)

Edit: It is easier to [COLOR=#0000ff]**make and better to have a casper-rw partition**[/COLOR].

I downloaded a bunch of the Live USB Install creators and used **Universal USB Installer** as it had an option to add the Casper RW File. I was **wondering how to convert this to a partition instead**?
**What should be the size and structure of this partition? FAT32 or Ext*? **

> **oldfred said:**
> **Pros & cons of persistence** install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I have one of the older versions of Ubuntu in a 16GB flash drive with 8GB for / (root) and 8GB for data where I have **other repair ISO** that I can **directly boot from grub**. I did not add swap as system(s) I was booting would not normally use swap as they had enough RAM. I **do change some settings to reduce writes**.
I think it would have been better to have used one of the **lighter weight flavors** like **Xubuntu or Lubuntu** as then flash drive would not be as large & have to load as much to boot.

The only time in recent history that I have created a flash drive installer was when I had my new system and no other way to boot  in UEFI mode and install. Most of my flash drives now are larger and have full installs or just ISOs to direct boot. I was _not sure how to create a **direct ISO boot** of **UEFI grub** from **BIOS**_ but now believe I could have.
What settings and how could I apply them? Is there a set of commandline options/ batch/ script I can run?

> **sudodus said:**
> I think all these tools work, at least for many people and in many computers. You can try more than one of them and compare the result. 

I have been developing ***mkusb version 10*** recently, and think it is a good alternative. It can create persistence for Ubuntu family desktop systems (32-bit as well as 64-bit systems) that run in BIOS mode as well as in UEFI mode. You can select maximum amount of available drive space for persistence, '100%'. It is not limited by the 4 GB max file size in the FAT32 file system.

[mkusb version 10]("https://help.ubuntu.com/community/mkusb#mkusb_version_10")

I agree with ***oldfred*** that you should use an Ubuntu flavour with an **ultra light desktop environment, Lubuntu**, or **Xubuntu with a medium light desktop environment**. This way more drive space will be available for installing programs, and in general, it will run faster (the USB interface is slower than that of internal drives).

I am considering trying Lu or Xu later. For now, I read through the amazing links you posted. From his CP's experiments it seems that the speed cant be improved in any "config"? Or am I wrong?

---

### Post by crashnburn_in on 2015-08-24
Also, how to bypass the "Install v/s Try" screen? Can I just have it default boot into UB GUI?

---

### Post by oldfred on 2015-08-24
More info on persistence.
       [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

    
With a full install, I edit fstab to have noatime. Then each time you access a file, it does not update the time accessed which saves writes which are very slow. But a very few apps like mutt may then have issues.

---

### Post by sudodus on 2015-08-25
> **crashnburn_in said:**
> I downloaded a bunch of the Live USB Install creators and used **Universal USB Installer** as it had an option to add the Casper RW File. I was **wondering how to convert this to a partition instead**?
**What should be the size and structure of this partition? FAT32 or Ext*? **

What settings and how could I apply them? Is there a set of commandline options/ batch/ script I can run?

I am considering trying Lu or Xu later. For now, I read through the amazing links you posted. From his CP's experiments it seems that the speed cant be improved in any "config"? Or am I wrong?

Please don't feel locked in by your present system on the pendrive. It is easy enough to start from scratch with a new system. If you use mkusb and install a persistent live system, you will get a system with a correctly formatted casper-rw partition (ext4 with journaling turned off).

Try it with Lubuntu :-)

---

### Post by sudodus on 2015-08-25
> **crashnburn_in said:**
> Also, how to bypass the "Install v/s Try" screen? Can I just have it default boot into UB GUI?

The 'Install v/s Try screen' will not appear with all systems. mkusb makes a system that boots via grub and you get to a grub menu, where the first and default option is to boot with persistence. It starts after ten seconds if you do not select another option.

---

### Post by efflandt on 2015-08-25
Although, a live/install iso with persistence can be more compact (since it boots from a compressed squashfs file system), it does not really have any security, since anyone can boot and use it (including sudo) with no password. But that fixed squashfs boot system also means that you cannot update anything (without remastering the iso) other than added programs (you cannot update kernel, add video drivers, or anything else that initially happens during boot). And although with persistence you can create another user that requires a password, you still cannot require a password for the default user "ubuntu".

8 GB used to be enough room for a full install. But even if you have enough RAM that you do not need swap, not sure how much room you will have after adding programs and doing updates. If you do a full install on flash memory you can take some tips from looking at /etc/fstab of the live/install system, like how it uses **tmpfs** (RAM) for **/tmp**, to save wear on flash memory, since everything is deleted from /tmp anyway whenever you boot. The only time tmpfs for /tmp would be an issue is if you do something that needs a lot of space in /tmp, like ripping a DVD, in which case if using tmpfs with not enough RAM you would need enough swap. Another good fstab option when using flash is **noatime**, so it does not write last access time for every file you just look at.

I have no swap on my 8 GB desktop (because booting is almost as quick as waking from suspend, much less hibernation) and it does not use much power if I just leave it idle instead. And I do not have swap on my 8 GB laptop (which boots Ubuntu quickly from mSATA SSD card). I actually do not even have swap on my 2 GB tablet PC because it only has a 32 GB SSD (Win7 Pro) and boots either Lubuntu or Ubuntu from separate partitions (with common /home partition) on 32 GB SD card. But I do not do anything demanding on that because it only as a 1 GHz 2 core cpu.

---

### Post by crashnburn_in on 2015-08-26
Its wierd how quickly I faced space issues on 2 live USB with Casper-RW persistence installs. - Is this the same as this link -[SIZE=2][ Live USB out of space?]("http://ubuntuforums.org/showthread.php?t=1448929") -[http://ubuntuforums.org/showthread.php?t=1448929](http://ubuntuforums.org/showthread.php?t=1448929) [/SIZE]

Are there any recent updated discussion threads on this subject?

1 - 8GB USB with Ubuntu
2 - 4GB USB with Easy2boot using Mint 13 Cinnamon live ISO

I have barely downloaded and installed small thing like GRSync, UltraCopier etc to use as Programs. 

The largest I am thinking is adding MATE to the 4G USB Flash with Mint 13. 

What kind of Casper space file should I create? How do I figure out the right amount?

---

### Post by crashnburn_in on 2015-08-26
Also, is there an easy way to add this Speed Boster to a NEW Live USB Persistent ? [SIZE=2][Making Ubuntu Fast using RAM (updated and simplified)]("http://ubuntuforums.org/showthread.php?t=1594694")[/SIZE] - This seems a bit old. Can it still be done?

---

### Post by sudodus on 2015-08-26
> **crashnburn_in said:**
> Its wierd how quickly I faced space issues on 2 live USB with Casper-RW persistence installs. - Is this the same as this link -[SIZE=2][ Live USB out of space?]("http://ubuntuforums.org/showthread.php?t=1448929") -[http://ubuntuforums.org/showthread.php?t=1448929](http://ubuntuforums.org/showthread.php?t=1448929) [/SIZE]

Are there any recent updated discussion threads on this subject?

1 - 8GB USB with Ubuntu
2 - 4GB USB with Easy2boot using Mint 13 Cinnamon live ISO

I have barely downloaded and installed small thing like GRSync, UltraCopier etc to use as Programs. 

The largest I am thinking is adding MATE to the 4G USB Flash with Mint 13. 

What kind of Casper space file should I create? How do I figure out the right amount?

I suggest that you try some different tools and settle with the system that fits your purpose best.

Do not add MATE, instead you should install a system that comes with MATE from the beginning. Otherwise you are wasting drive space and effort :-)

I recommend a casper-rw ***partition*** as described in previous posts. In your case I also recommend a bigger USB pendrive - at least 16 GB. It is also easier to find USB 3 pendrives with fast flash memory among pendrives with 16 and 32 GB size memory, and fast flash memory makes a big difference when booting and running from USB.

---

### Post by sudodus on 2015-08-26
> **crashnburn_in said:**
> Also, is there an easy way to add this Speed Boster to a NEW Live USB Persistent ? [SIZE=2][Making Ubuntu Fast using RAM (updated and simplified)]("http://ubuntuforums.org/showthread.php?t=1594694")[/SIZE] - This seems a bit old. Can it still be done?

Post a question in that thread! Unless the creator of the system is away (for example travelling during holidays), I think you will get a reply soon.

I think you get a long way to run in RAM with a live (or persistent live) system, if you simply use the boot option **toram**. You need enough RAM of course.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

