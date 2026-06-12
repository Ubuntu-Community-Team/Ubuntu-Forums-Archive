---
title: "noob question about ubuntu installation"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by bavman on 2011-07-03
I havent dabbled in linux for a while, but i need it now so im trying to install it again. The harddrive i want to install to isnt my primary hd, and also has another os on it. So i partitioned ~200gb for ext4 and ~15gb for linux swap. Is that all i need to have? 

Then when i get to the "allocate drive space" in the installation do I just click ext4 and hit install now? 
I set the ext4 partition as ext4 journaling system and mount point as "/". Is that correct? 

Also at the bottom is asks for device for boot loader installation. What if I dont want to install this? The harddrive im installing to already has its own boot loader (chameleon for osx), and I dont want to mess with my other harddrive which has windows 7 and its mbr. Chameleon should be able to pick ubuntu right? 

Thanks for all the help and sorry for the noob questions

---

### Post by oldfred on 2011-07-03
I prefer smaller / (root) or system partitions for all systems and separate data or /home to store data. System is slightly more efficent as it does not have to search large partition to find files. But you need to have only 25% used. I find with lots of programs I am using about 6GB, so a 20 to 25GB root is good. Then the rest of the space for /home. Swap can be as little as 2GB or if hibernating then the same size as RAM in GiB. If lots of RAM you probably will not (and do not want to) be using swap.

To keep your boot loader in the MBR, manually partition in advance or as part of the install. 11.04 now calls it "Something Else". then you also get to select where to install grub2's boot loader. I would install to the PBR partition boot sector. That is not normally recommended as it is less reliable. You may have to reinstall after grub updates. It has to use blocklists or hard coded addresses to find files as PBR is too small to hold all the code it would like to have or normally has.

Do you have gpt partitions? If so you can can create a bios_grub partition and if so you cannot install to the partition as gpt does not support PBRs. Not sure if that totally works or not. I directly boot from BIOS MBR to my Ubuntu with gpt and have a bios_grub partition.

---

### Post by dFlyer on 2011-07-03
> **bavman said:**
> I havent dabbled in linux for a while, but i need it now so im trying to install it again. The harddrive i want to install to isnt my primary hd, and also has another os on it. So i partitioned ~200gb for ext4 and ~15gb for linux swap. Is that all i need to have? 

Then when i get to the "allocate drive space" in the installation do I just click ext4 and hit install now? 
I set the ext4 partition as ext4 journaling system and mount point as "/". Is that correct? 

Also at the bottom is asks for device for boot loader installation. What if I dont want to install this? The harddrive im installing to already has its own boot loader (chameleon for osx), and I dont want to mess with my other harddrive which has windows 7 and its mbr. Chameleon should be able to pick ubuntu right? 

Thanks for all the help and sorry for the noob questions

This will work, if you don't want to use a separate /home directory.

---

### Post by shanjay86 on 2011-07-04
this is wht i did small root

---

### Post by srs5694 on 2011-07-04
> **oldfred said:**
> Do you have gpt partitions? If so you can can create a bios_grub partition and if so you cannot install to the partition as gpt does not support PBRs. Not sure if that totally works or not. I directly boot from BIOS MBR to my Ubuntu with gpt and have a bios_grub partition.

Support for partition boot records (PBRs) is a function of the boot loader, not of the partitioning system. A typical GRUB 2 configuration on GPT on a BIOS-based computer places GRUB files in the MBR, in the BIOS Boot Partition (marked as "bios_grub" in GParted or parted), and as files in the Linux boot partition. AFAIK, GRUB 2 doesn't use PBR code on a GPT system, although there might be circumstances in which it does. Likewise, typical UEFI boot loaders don't rely on PBR boot code, at least not to boot an OS in UEFI mode, although in theory they could.

[SYSLINUX,](http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project) OTOH, has an MBR-resident GPT boot loader for BIOS-based systems that requires PBR support. The SYSLINUX GPT loader is similar to the DOS/Windows or SYSLINUX MBR boot loader, in that it searches for a partition with a particular attribute set ("Legacy BIOS Bootable" in the case of GPT) and runs that partition's PBR code. I don't know offhand if it could launch either GRUB Legacy or GRUB 2 in this way, but if not that's a GRUB limitation, not a GPT limitation. The one configuration in which I've used SYSLINUX's GPT loader is to launch [BootDuet,]("https://github.com/migle/BootDuet") which is resides in a FAT partition's PBR and in turn launches [UEFI DUET,]("https://gitorious.org/tianocore_uefi_duet_builds/tianocore_uefi_duet_installer/trees/master") which effectively turns a BIOS-based computer into a UEFI-based computer. (I describe this setup [here,]("http://www.rodsbooks.com/bios2uefi/index.html") if you're interested.) This configuration works and it can even be used to install and boot Ubuntu, but using GRUB 2 in the more conventional way on GPT disks is much simpler.

---

