---
title: "install ubuntu (or a flavor) on a diferent drive and let regular bios boot mgr choose"
date: 2015-06-05
forum: Installation &amp; Upgrades
---

### Post by christopher-acosta-af on 2015-06-05
is it possible to install Ubuntu on a different drive without grub and just use BIOS boot drive choosing to switch between windows on 1 drive and ubuntu on another?

---

### Post by grahammechanical on 2015-06-05
If we install Ubuntu or one of the other Ubuntu family members on its own hard drive without Grub then we will not be able to load Ubuntu. Grub is the boot loader. We can use the BIOS boot system to select which hard drive to boot from but all we would get is an error message saying that the machine could not find an OS. And that is because we need a boot loader to direct the machine to the Linux OS.

It is possible to install Ubuntu on another drive but there is one thing that we have to watch out for. By default the installer will put the Grub boot loader into the MBR of first hard drive (sda, as it is called in Linux). If Ubuntu is going on the second hard drive (sdb) then we need Grub to be installed into the MBR of sdb.

Then we will have a Windows drive with its boot loader and a Ubuntu drive with its boot loader and we can use the BIOS to select which drive to boot from.

The simple way to do this is to disconnect the Windows drive and then install Ubuntu on the second drive using the Erase disk and install Ubuntu option. Then reconnect the Windows drive, use the BIOS to load into Ubuntu and run

```
sudo update-grub
```

and we will have a Grub boot menu that will list the Windows boot loader as an option from which we can load Windows and only use the BIOS menu option if we need to or desire to. And we will still have a Windows boot loader on the Windows drive to load Windows should anything happen to the Ubuntu drive.

There is another method using the Something Else option. But it is a bit more complicated to explain and to do.

Regards.

---

### Post by christopher-acosta-af on 2015-06-05
> **grahammechanical said:**
> If we install Ubuntu or one of the other Ubuntu family members on its own hard drive without Grub then we will not be able to load Ubuntu. Grub is the boot loader. We can use the BIOS boot system to select which hard drive to boot from but all we would get is an error message saying that the machine could not find an OS. And that is because we need a boot loader to direct the machine to the Linux OS.

It is possible to install Ubuntu on another drive but there is one thing that we have to watch out for. By default the installer will put the Grub boot loader into the MBR of first hard drive (sda, as it is called in Linux). If Ubuntu is going on the second hard drive (sdb) then we need Grub to be installed into the MBR of sdb.

Then we will have a Windows drive with its boot loader and a Ubuntu drive with its boot loader and we can use the BIOS to select which drive to boot from.

The simple way to do this is to disconnect the Windows drive and then install Ubuntu on the second drive using the Erase disk and install Ubuntu option. Then reconnect the Windows drive, use the BIOS to load into Ubuntu and run

```
sudo update-grub
```

and we will have a Grub boot menu that will list the Windows boot loader as an option from which we can load Windows and only use the BIOS menu option if we need to or desire to. And we will still have a Windows boot loader on the Windows drive to load Windows should anything happen to the Ubuntu drive.

There is another method using the Something Else option. But it is a bit more complicated to explain and to do.

Regards.
Removing the main drive isn't an option, I'm trying to do this on a tablet that came with a hard drive on the dock, the main drive is an emmc chip so it can't be removed

---

### Post by ubfan1 on 2015-06-05
Then "something else" would be the option to choose.  Is this a UEFI machine? Is this a 32 bit UEFI (much harder).  What model?

---

### Post by christopher-acosta-af on 2015-06-06
> **ubfan1 said:**
> Then "something else" would be the option to choose.  Is this a UEFI machine? Is this a 32 bit UEFI (much harder).  What model?
yes it's a 32 bit uefi machine. I already got the live usb working, I can boot live fine already (so the iso is ready for install), I just want it installed on my dock's harddrive. its an asus t100ta

---

### Post by sudodus on 2015-06-06
1. It is risky to install a new operating system while your drive with the current operating system is connected. So I recommend that you ***backup*** your current operating system, or at the very least your personal files (documents pictures etc).

2. Boot from the Ubuntu install drive. Use ***gparted*** to create partitions for Ubuntu. A basic installed system has one root partition and one swap partition. If you want to hibernate, the swap partition should be at least as big as the RAM (in Mibibytes). Otherwise it is probably enough with 1 GB swap (and the rest of the drive can be used for the root partition).

3. Start the installer. Select ***Something else*** at the partitioning window, and select the partition you want to be the root partition '/'. 

I repeat the warning by grahammechanical and make it more detailed:

By default the installer will put the Grub boot loader into the MBR of  first hard drive (sda, as it is called in Linux). If Ubuntu is going on  the second hard drive (sdb) then we need Grub to be installed into the  MBR of sdb. This is done ***at the bottom*** of the partitioning page (below the selection of partitions).

---

### Post by christopher-acosta-af on 2015-06-06
I successfully installed it on a different drive without affecting the windows partition. however the Ubuntu partition wont boot.

---

### Post by sudodus on 2015-06-07
> **ubfan1 said:**
> Then "something else" would be the option to choose.  Is this a UEFI machine? Is this a 32 bit UEFI (much harder).  What model?

> **christopher-acosta-af said:**
> yes it's a 32 bit uefi machine. I already got the live usb working, I can boot live fine already (so the iso is ready for install), I just want it installed on my dock's harddrive. its an asus t100ta

> **christopher-acosta-af said:**
> I successfully installed it on a different drive without affecting the windows partition. however the Ubuntu partition wont boot.

- Did you install in UEFI mode?
- Did you install a 32-bit system (and not a 64-bit system)?

Installing Ubuntu in a 32-bit UEFI machine is 'much harder' as stated by ubfan1. I have not done it, because I have no such machine. But obviously your Ubuntu USB boot drive works.

- Until you manage to make a full installation, you might run Ubuntu as a persistent live system.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

- Maybe it works for you to use the method described at the following link. It is designed to be used to boot in UEFI mode from iso files, and it works also with 32-bit iso files. So if you create a menuentry (copy&paste&tweak) for the installed system, it might get your system running after some tweaks :-)
[URL="http://ubuntuforums.org/showthread.php?t=2276498"]
How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images[/URL]

---

### Post by christopher-acosta-af on 2015-06-07
> **sudodus said:**
> - Did you install in UEFI mode?
- Did you install a 32-bit system (and not a 64-bit system)?

Installing Ubuntu in a 32-bit UEFI machine is 'much harder' as stated by ubfan1. I have not done it, because I have no such machine. But obviously your Ubuntu USB boot drive works.

- Until you manage to make a full installation, you might run Ubuntu as a persistent live system.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

- Maybe it works for you to use the method described at the following link. It is designed to be used to boot in UEFI mode from iso files, and it works also with 32-bit iso files. So if you create a menuentry (copy&paste&tweak) for the installed system, it might get your system running after some tweaks :-)
[URL="http://ubuntuforums.org/showthread.php?t=2276498"]
How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images[/URL]

I installed a 64 bit version on my 64 bit processor machine running 32 bit windows... I could not find ANY instructions on making a usb uedi bootable 32 bit ubuntu so I chose 64 bit.

I have no idea how to install ubuntu in uefi mode, I disnt see that option anywhere in the install wizard. 

This seems to complicated, I remember when ubuntu was as easy as loading it into a disk and installing it. Since ubuntu cant figure out how to make 32bit uefi machine installation user-friendly I guess im giving up on installing linux. Shame I kinda liked the OS ubtil they couldn't keep up with technology.

---

### Post by sudodus on 2015-06-07
> **christopher-acosta-af said:**
> ... Shame I kinda liked the OS ubtil they couldn't keep up with technology.

I think it is not quite like that. I think that some manufacturers make their system such that it should be hard to run anything but Windows. They tweak the UEFI system beyond the UEFI standard. I don't think the problem is 'keeping up with technology', but trying to work around the obstacles created by some manufacturers.

Many major manufacturers make modern computers, that work well with Ubuntu and other linux distros.

-o-

By the way, I tweaked a multiboot system for UEFI today, so that it boot also in BIOS mode. I was able to run Xubuntu that way in an old Dell with Pentium 4. But the same system runs the same 32-bit Xubuntu in UEFI mode. Maybe you can try if it works for you.

See this link [http://ubuntuforums.org/showthread.php?t=2276498&p=13299549#post13299549](http://ubuntuforums.org/showthread.php?t=2276498&p=13299549#post13299549)

-o-

If I understand correctly, you can run a live session with Ubuntu, 'Try Ubuntu without installing'. In this case the simplest method might be to make a persistent live system: Create a partition with the ext2 file system and the label **casper-rw**.

Boot your USB install drive with Ubuntu and use the boot option **persistent**, and you get a persistent live system, so that you can save files, and install application program packages. But you cannot install new kernels.

---

### Post by oldfred on 2015-06-07
The only other 32 bit UEFI I have seen.

 Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)

You used to have to recompile everything like the bad old days.

 Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Sound issues on Bay Trail
[http://ubuntuforums.org/showthread.php?t=2255425](http://ubuntuforums.org/showthread.php?t=2255425)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

I think since Linux did not have 32 bit UEFI support until recently, Microsoft thought they could lock users into Windows only. They really want to be like Apple's iPad where it just about is impossible to use anything else. 
So when you purchase one of these non-standard configurations, you need to assume it is only going to work with whatever the vendor supplies.

---

