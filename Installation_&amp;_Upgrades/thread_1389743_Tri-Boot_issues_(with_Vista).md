---
title: "Tri-Boot issues (with Vista)"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by erictherev on 2010-01-24
I have an Acer Aspire One 0751h netbook that I am attempting to install three operating systems on. The end result will hopefully net me Vista, XP Pro and Kubuntu 9.10. I have installed all three numerous times, and I can only get two working at a time. I can have Vista and Kubuntu or XP and Kubuntu. I believe the problem lies with XP putting the MBR on sda1, but Vista formats this drive completely during installation. I am installing Vista using an Acer OEM CD, XP is a full version disc, and Kubuntu is a live CD. Vista requires  a Windows drive letter of C:, so I'm putting it on sda1.

Here is the partitioning scheme I am working with:

Vista  **|**  swap  **|**  XP Pro  **|**  Kubuntu  **|**  storage
 sda1  **|**  sda2  **|**   sda5   **|**    sda6   **|**   sda4
 NTFS  **|**  swap  **|**   NTFS   **|**    ext4   **|**   NTFS

I have tried installing XP then Vista, as is the general online consensus of how to do this, but then after installing Kubuntu only Vista is recognized.

I have no problem with formatting any or all of the partitions and reinstalling any or all of the OS's. I just want this to work and reinstalling may or may not be the simplest solution.

Factors I believe to be contributing to my problems:

**1)** Grub2 is not made to be manually edited, as Grub-legacy is.
**2)** Grub2 does not detect both XP and Vista when I run grub-update.
**3)** Vista insists upon being located in the first partition.
**4)** XP puts boot.ini in the first partition.
**5)** My Acer OEM Vista disc does not allow for a repair, just a complete reinstall.
**6)** If I install XP prior to installing Vista, the first partition will be formatted, removing boot.ini.
**7)** Vista does not use boot.ini. This has been replaced with the BCD (Boot Configuration Data).

Any help or ideas would be greatly appreciated.

---

### Post by erictherev on 2010-01-24
Am moving this thread here:

[http://ubuntuforums.org/showthread.php?t=1389417](http://ubuntuforums.org/showthread.php?t=1389417)

---

### Post by Mark Phelps on 2010-01-25
> **erictherev said:**
> Factors I believe to be contributing to my problems:

[1) Grub2 is not made to be manually edited, as Grub-legacy is.
So? That's how it works.  There are plenty of links on how to manually edit the GRUB2 stuff.  In my case, despite the presence of several OS's and several drives, update-grub worked find and found ALL the OS's on my machine.
> 2)Grub2 does not detect both XP and Vista when I run grub-update. 
You didn't say what it DID detect.  I suspect it detected only one because, I'm willing to bet that your MS Windows boot files are really in one partition, not two -- which means that GRUB2 is working properly.
>  3) Vista insists upon being located in the first partition. MS is rather inflexible about where stuff needs to go.
> 4) XP puts boot.ini in the first partition. Every MS Windows OS I've ever installed insists on putting the loader files in the first MS-Windows-compatible partition it finds.  See 3) above. 
> 5)My Acer OEM Vista disc does not allow for a repair, just a complete reinstall.  That's how these things work.
> 6)If I install XP prior to installing Vista, the first partition will be formatted, removing boot.ini. See 4) above -- that's what it does.
>  7) Vista does not use boot.ini. This has been replaced with the BCD (Boot Configuration Data).Welcome to the world of Vista -- Win7 does exactly the same thing. 

What you're discovering is the MS is rather inflexible with lots of things it does by default when installing OS's.  That's why many of us have come over to the Linux community -- a lot more say in where stuff goes and how it works.

---

### Post by erictherev on 2010-01-25
OK, so all of my boot loader type files are scattered across three partitions.

My current thought is to take the XP boot loader files and move them to my XP partition. Then I would boot into Kubuntu from the live CD (since Grub is currently broken) and do a Grub repair from the CD. If I move the XP boot files from my Vista partition to my XP partition, would these files work? If so, what would I need to move in addition to boot.ini?

Thanks in advance for any help.

---

### Post by Leppie on 2010-01-25
if you want different boot managers for all systems, your best bet would be:
1 install vista in first partition
2 create a second primary partition for xp and set it to bootable (this should prevent xp from putting the boot loader into vista's partition and merge the 2 boot loaders). you will still have sda3 to create the extended partition.
3 install xp into the newly created partition
4 install ubuntu wherever you want and install grub2 into the mbr so it can chainload the 2 windows versions and (k)ubuntu

---

### Post by erictherev on 2010-01-25
> **Leppie said:**
> if you want different boot managers for all systems, your best bet would be:
I'm not really sure I care about the boot manager. I just want to be able to boot all three.
> **Leppie said:**
> 1 install vista in first partition
2 create a second primary partition for xp and set it to bootable (this should prevent xp from putting the boot loader into vista's partition and merge the 2 boot loaders). you will still have sda3 to create the extended partition.
If I set the XP partition to be bootable, will this interfere with my ability to see the Vista partition when running XP?
> **Leppie said:**
> 3 install xp into the newly created partition
4 install ubuntu wherever you want and install grub2 into the mbr so it can chainload the 2 windows versions and (k)ubuntu
Knowing very little about command-line partitioning, I'm using [this guide]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html") to set the XP partition to be bootable. It's slow due to formatting, but I'm getting there.
I love the fact that I'm in a Linux community forum getting straightforward answers about Windows, when I can't get the same answers from M$. :twisted:

---

### Post by Leppie on 2010-01-25
being able to see the vista partition does not depend on the boot flag, it depends on the filesystem type and if the partition is set to be hidden.

---

### Post by erictherev on 2010-01-26
OK, I formatted the drives using linux fdisk, installed Vista, rebooted into 9.10 live CD, set sda3 (XP partition) as bootable, unset sda1 (Vista partition) as bootable, rebooted into XP install CD and installed XP.

Apparently, when I installed XP, it unset my boot flag and set a boot flag on sda1. The boot loader files for XP are once again on sda1, so I'm right back where I was.

Assuming that Windows will not remove any files it needs to run, I'm currently formatting my Vista partition from within XP. Then anything left over will be what XP requires to boot. If that doesn't work, I'll do a repair or reinstall of XP with my Vista partition blank. Either way, any files left in the Vista partition will be required for XP to boot, and I'll know which files to move to my XP partition.

---

### Post by Leppie on 2010-01-26
you will have to set the boot  flag on your xp partition prior to restoring the boot loader. not setting the boot flag to the xp partition will result in restoring the boot loader to sda1. setting the boot flag to a different partition removes the boot flag from the partition that is currently holding the boot flag. there can be only 1 partition with the boot flag.

---

### Post by erictherev on 2010-01-26
> **Leppie said:**
> you will have to set the boot  flag on your xp partition prior to restoring the boot loader. not setting the boot flag to the xp partition will result in restoring the boot loader to sda1. setting the boot flag to a different partition removes the boot flag from the partition that is currently holding the boot flag. there can be only 1 partition with the boot flag.

I actually had the XP drive flagged, but somehow XP unflagged it during installation and flagged the Vista partition. So, I formatted the Vista partition and reinstalled XP (hal.dll disappeared as well as all of the other boot files not being where installation put them). After reinstalling XP, I flagged the Vista partition and am now reinstalling Vista.

Continuing with this process, I will hopefully have Vista (flagged as boot) on sda1, XP on sda3 and Kubuntu on sda4. Once XP and Vista are installed, Grub should detect both and I'd be able to boot any of the three with Grub.

---

### Post by erictherev on 2010-01-26
OK, so I installed XP first, with that partition flagged as boot. Then I installed Vista, with that partition flagged as boot. Finally, I installed Kubuntu. In a nutshell...

flag sda3
install XP
flag sda1
install Vista
install Kubuntu

I now have all 3 working and all three boot from grub.

Thanks for the help, Leppie!

---

### Post by Leppie on 2010-01-27
you're very welcome, glad it's all working properly :)

---

