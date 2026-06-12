---
title: "Install from ISO on Linux to USB w/o reboot"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by wolfgentleman on 2014-06-08
OK, I am currently running Kubuntu Saucy. I have scoured without success on how to install Ubuntu/Debian from an ISO onto a flash drive without rebooting. Now I don't want to use something like UNetbootin, as that installs *the ISO/live CD*, not the full OS. I tried mounting the ISO and running the Windows executable in wine, but the exe crashed because of "kernel" issues. Any ideas?

---

### Post by ajgreeny on 2014-06-08
I'm not quite sure what you are asking here, but I don't think it is possible to install direct from an .iso image file without first burning the image to either a DVD or making an installation USB drive.

It is possible to run a full installation, rather than a live OS, on to a flash drive from that burned DVD or USB, by using the "Something Else" option at partitioning stage and choosing the USB as the drive for the partitions needed, and also, very importantly, for the bootloader.

If you choose to do this, be warned that a flash drive is not ideal for a journalled file system such as ext4, as the number of writes will probably be excessive and could cause early disk failure.

---

### Post by wolfgentleman on 2014-06-08
> **ajgreeny said:**
> [COLOR=#000000]I'm not quite sure what you are asking here[/COLOR]
[COLOR=#000000]I have an 2 ISOs with different distros on them: Kubuntu i386 and Kali Linux i386. How can I install them on my flash drive without rebooting to them?[/COLOR]

> **ajgreeny said:**
> I don't think it is possible to install direct from an .iso image file without first burning the image to either a DVD or making an installation USB drive
It is. I found [this]("http://askubuntu.com/a/340171") in my rummaging, but it requires a reboot. Another option if I am going to do it that way, is to use UNetbootin to install them on a different drive and boot onto it and install it on the target drive.

> **ajgreeny said:**
> It is possible to run a full installation, rather than a live OS, on to a flash drive from that burned DVD or USB, by using the "Something Else" option at partitioning stage and choosing the USB as the drive for the partitions needed, and also, very importantly, for the bootloader.
Yeah, I always do that anyway as I'm picky about my partitions. I already have it partitioned how I want it, I just need to install the OSes. It will be my (nearly) universal toolkit drive.

> **ajgreeny said:**
> If you choose to do this, be warned that a flash drive is not ideal for a journalled file system such as ext4, as the number of writes will probably be excessive and could cause early disk failure.
Really? Hmm... Maybe that's why my other USB drive died after 3 years of use... Not much shame for though, it served well... It works every once in a while, but not reliably. Thanks for the tip, I will keep it in mind.

---

### Post by C.S.Cameron on 2014-06-08
You can use something like MultiBootUSB, [http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273), to boot iso files located on a flash drive.
Once booted you can do a Full install from most of these.

If you do the math based on a minimum life of 10000 writes to flash drive you should find there is not much chance of wearing one out.
I have a Kingston that I have been booting Linux from since 2006.

---

### Post by oldfred on 2014-06-09
I manually install grub to a flash drive and copy ISO to a folder. Then I can boot as many ISO as I can fit on drive.
I started before many of the scripts were created that automate it. I prefer grub and only one or two of scripts use grub, others use syslinux or other boot loaders.

I also have full install on a flash drive. And in a data partition I have a couple of ISO to be added repair tools like Knoppix, gparted, parted magic, Supergrub etc.

I do use ext4 but turn off journal as partition is small and it is just an install with not a lot of data. I also change a few settings in fstab to reduce writes.

I find USB3 flash drives are still about 10% faster in my USB2 ports than USB2 flash drives. But brand matters.

       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by wolfgentleman on 2014-06-09
> **C.S.Cameron said:**
> You can use something like MultiBootUSB, [http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273), to boot iso files located on a flash drive.
Once booted you can do a Full install from most of these.
Well, if I am going to reboot I will use the grub method I linked.

> **C.S.Cameron said:**
> If you do the math based on a minimum life of 10000 writes to flash drive you should find there is not much chance of wearing one out.
I have a Kingston that I have been booting Linux from since 2006.
OK, cool. Kingston's a good brand. In fact, that's what the one I'm working with is. :p 64 GB Kingston, slim with metal outer-casing (ruggidized) and a 5 year limited warranty. And the price tag was nice: $25

Anyway, I will delay a little further should any answers come up.

---

