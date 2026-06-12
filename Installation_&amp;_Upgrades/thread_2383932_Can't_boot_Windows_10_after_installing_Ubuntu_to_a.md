---
title: "Can't boot Windows 10 after installing Ubuntu to a different HDD (non dual boot)"
date: 2018-01-31
forum: Installation &amp; Upgrades
---

### Post by civicg7 on 2018-01-31
Hello! It's my first post here, hope I'm not breaking any rules.
So the problem is the following: I decided to install Ubuntu 16.04.3 LTS on an old HDD (gonna call it "HDB") I have, while keeping my Mycrosoft 10 OS on my main disk ("HDA"). I downloaded Ubuntu ISO from the official site, and put it on a bootable 8gb pendrive using Rufus. Then I formatted HDB using the simple (don't know how to call it) way by right clicking the drive on Computer and choosing "format" option. After formatting I restarted the PC and it booted Windows just fine. Everything went well to this point, so I restarted again and proceeded to install Ubuntu. When first trying to install it I couldn't go much further than selecting the install option because I was getting some usb errors (error 62 and 110 if I am not mistaken), which I later solved by googling and testing to discover that my USBs 2.0 ports were not working properly¹, but then I used the 3.0 ports and loaded the installer just fine. So at the installing process I couldn't really find a way to install it on the HD I wanted (couldn't be sure where it was going to install tbh) then to be safe I cancelled, shutted the PC down, removed the SATA (and power) cable from HDA and launched the installation again, later on the installation I choose the method to “normally” install Ubuntu (not in dual boot mode) and a prompt appeared saying that there were some Windows folders (or partitions maybe? Can't remember the word) on HDB which I found strange but was pretty sure had nothing to do with my Mycrosoft 10 installation since It was on HDA, so I continued and “forced” (this word showed on another prompt) the installation. After it finished Ubuntu was working well so I shutted it down, removed HDB SATA and power, and plugged HDA SATA and power cables back in to access Windows 10 again but now I’m receiving the “Reboot and select proper boot device or insert boot media in selected boot device and press a key”.
So how do I proceed? I’ve done some searching and found similar problems to mine but not the exactly the same. I think a good start should be trying to use Linux Boot-Repair? Maybe running Windows Boot repair tool with a bootable pendrive? I’ve just done nothing at the moment because I’m afraid of making things worse, so I’m looking for proper advice.

I ran some code lines I saw on other topics that may help with the diagnostic: [https://paste.ubuntu.com/26495333/](https://paste.ubuntu.com/26495333/)

My BIOS config bellow:
[ATTACH=CONFIG]278397[/ATTACH][ATTACH=CONFIG]278398[/ATTACH]

Sorry for the lack of more technical info or if it looks confusing, I’m a just a noob when it comes to IT, I only know how to do some formatting, partitioning, OS installing and know a little of hardware, but that’s all, I have zero programming background. And sorry for any grammar mistake, English is not my first language. Thank you in advance.

1 - It seems like my MOBO (G970A DS3P FX) does not work well with Linux.

---

### Post by oldfred on 2018-01-31
You have a new UEFI based system.

Your sda drive is gpt partitioned which normally is used with UEFI. But it does not have the normal partitions that Windows uses for UEFI boot. Windows only boots in UEFI mode from gpt partitioned drives. And partitions do not look like an old BIOS install either.

Or you do not show Windows. Was Windows really on sdb drive? Which now has your Ubuntu install.

You also used the advanced LVM full drive install option. Some advanced users like it, and it is required if you want full drive encryption. But otherwise not really recommended for new users as standard partitioning tools can only be used for a few things and LVM tools must be used for most things with Logical volumes.

And using LVM erased entire drive, so whatever was on it is now gone.

Your motherboard needs to have latest UEFI from vendor, changes to UEFI settings, and some boot parameters.
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by civicg7 on 2018-01-31
> **oldfred said:**
> You have a new UEFI based system.

Your sda drive is gpt partitioned which normally is used with UEFI. But it does not have the normal partitions that Windows uses for UEFI boot. Windows only boots in UEFI mode from gpt partitioned drives. And partitions do not look like an old BIOS install either.
Yes, I installed Windows 10 on HDA (sda) using the UEFI system (even needed to convert it from mbr using some commands on windows PE iirc).

> **oldfred said:**
> Or you do not show Windows. Was Windows really on sdb drive? Which now has your Ubuntu install.
I think there probably was a Windows 10 installation on HDB (sdb). I was using HDB (sdb) for a short time last year when my other HD broke, but it was not being used since I got this new HD (HDA/sda) and I was using the Windows 10 on HDA just fine for some months without HDB not even being plugged in the MOBO. 


> **oldfred said:**
> Your motherboard needs to have latest UEFI from vendor, changes to UEFI settings, and some boot parameters.
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Thank you very much for the links, I will be taking a better look at it later. I thought of updating the BIOS in the past but I've been told that to update the BIOS you need to flash it and that's not a very safe thing to do, is that true?

Thank you for answering!

---

### Post by oldfred on 2018-01-31
There are many comments on how dangerous it is to update BIOS/UEFI.
But I always do it and have never had an issue.
And a lot of the newer UEFI systems have dual UEFI/BIOS or ways to recover if an issues.
And most systems need updates to fix issues.

Main issue on update is if you have a power failure in the middle of the update, so it only partially completes. Then you may have an issue.
So I do not update in middle of thunderstorms.  (But have had power failure on sunny days.)

---

### Post by civicg7 on 2018-01-31
Ok, I followed the link's proceedment and fixed the USB issue, thank you very much! However, Windows boot problem persists... I'm still getting the "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key". Is it possible that there was actually boot files from Windows 10 installation (wich was on HDA/sda) on HDB (sdb) and I was somehow able to boot Windows 10 without even having HDB (sdb) connected to the MOBO? Because I'm 100% sure I disconnected both SATA and power cables from HDA (sda) when installing Ubuntu to HDB (sdb).

---

### Post by oldfred on 2018-01-31
That is what it looks like.

You do not have an ESP which Windows would have for UEFI boot. So even if the NTFS partition on sda is Windows it has no way to boot.

Your Ubuntu install is BIOS, so you have to in your UEFI turn off UEFI, turn off UEFI Secure boot (which maybe Windows/Other setting with no mention of secure boot) and/or turn on BIOS/Legacy/CSM boot.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

For both Windows & Ubuntu, how you boot install media UEFI or BIOS is then how it installs. Best to always boot in one mode or the other.
And default setting for internal drive does not apply to booting USB flash drive. For USB flash drive, you will normally have two boot options, one UEFI and one not UEFI or BIOS.

---

### Post by civicg7 on 2018-01-31
Ok, I tried to run boot-repair from BIOS Ubuntu but got stuck on a error saying "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.". I googled it and it seems that this error occurs if you try to launch the boot-repair tool with a BIOS Linux installation while having a GPT partition installed as well, so I launched a live-usb Ubuntu in UEFI (I changed the configs in setup to boot UEFI only), downloaded boot-repair again, launched it and got the same error (!). Went to look how to be certain I was on UEFI Ubuntu mode and found some commands to check, ran them, and it seems it is indeed in UEFI mode:

ubuntu@ubuntu:~$ /sys/firmware/efi
bash: /sys/firmware/efi: Is a directory
ubuntu@ubuntu:~$ dmesg | grep "EFI v"
[    0.000000] efi: EFI v2.31 by American Megatrends

Why do I still get the GPT detected error? Do you know how to fix it? Does it not work with live-usb Ubuntu?

---

### Post by oldfred on 2018-01-31
While Ubuntu is installed on sdb, your sda drive is gpt.

The default fix with Boot-Repair and BIOS mode is to install grub to MBR of all drives. Generally with two or more drives you may want different boot loaders in each drive. Or do not use default repair, but use advanced mode and choose operating system and choose drive to install boot loader into.

You can also eliminate the error by adding a bios_grub partition, 1 or 2MB unformatted on your gpt drive.
I used to only have BIOS system but converted to gpt back in 2011. And had to add bios_grub partition to every drive. Even before I had UEFI but Windows was having all new systems (2012) use UEFI with gpt partitioning I started making all new or totally reformatted drive gpt but with both an ESP - efi system partition for future use, and I still add a bios_grub partition even though systems are now UEFI.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by civicg7 on 2018-01-31
Boot-repair details report: [https://paste.ubuntu.com/26497197/](https://paste.ubuntu.com/26497197/)
I ran it using the live USB Ubuntu (which should be running in UEFI mode), downloaded the boot-repair tool following the instructions listed on [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info).
If I add this bios_grub partition to my Windows GPT drive (sda) will boot-repair try to fix the boot and enable it to keep booting with UEFI normally(if it succeeds to fix the boot problem, of course)? Thank you.

---

### Post by oldfred on 2018-01-31
No, bios_grub on gpt partitioned drives is just for installing grub for booting in BIOS boot mode. And you do not need and probably should not have grub installed to the Windows drive.
If you want UEFI boot you must have an ESP - efi system partition.

If you set system for BIOS boot or UEFI off, can you boot sdb/Ubuntu drive?

Your UEFI is not showing an entry for Windows boot. But when you disconnect a drive, UEFI forgets entries for that drive.
So I have no way of knowing if your Windows install was UEFI or BIOS.
And you want same boot mode for Ubuntu and Windows, both UEFI or both BIOS.

Boot-Repair also will not fix your Windows issues. You need extra partitions whether UEFI or BIOS and Windows can be particular about them.
If Windows was original BIOS boot on MBR and drive was somehow converted to gpt, you still need the Windows boot files that normally are in the Windows boot partition, which users do not see from Windows.

Your current Windows looks like neither of these typical Windows partition plans.
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by civicg7 on 2018-01-31
> If you set system for BIOS boot or UEFI off, can you boot sdb/Ubuntu drive?
Yes, setting system to both UEFI or Legacy and Legacy Only enable me to boot Ubuntu normally.

> Your UEFI is not showing an entry for Windows boot. But when you disconnect a drive, UEFI forgets entries for that drive.
So I have no way of knowing if your Windows install was UEFI or BIOS. 
I am pretty sure that I installed Windows 10 on UEFI mode, or at least I tried to, I needed to convert sda from MBR to GPT on Windows PE DiskPart to install Windows 10 as it was trying to install in UEFI mode and wouldn't let me install it on a MBR drive.

So looking at the links you sent me and comparing my drive partitions it seems that I only have a Windows partition and somehow managed to delete the other 3  (System, MSR and Recovery) when installing Ubuntu. I guess that's not a Ubuntu related problem anymore, but do you know if it is possible to recreate those 3 lacking partitions (via Windows PE DiskPart, for example) and restore  my Windows 10 installation or it's only possible to do a clean install to make it work again? Thank you very much for your help, I learned a lot today.

---

### Post by oldfred on 2018-01-31
Windows likes to have partitions in order.
Or generally ESP, then system reserved, and then main install. With vendor installs there are several recovery partitions.
ESP was 100MB, it may be larger with newer installs, sys reserved is 128MB.

But ESP does not have to be first partition. But I would then not make windows too large as ESP cannot be past some point on drive or UEFI may not see it.
Do not know about moving NTFS partitions, but any change does require chkdsk afterwards.

I would try to use Windows tools or perhaps Windows third party tools to make changes. Linux tools work best for Linux.

---

### Post by civicg7 on 2018-02-04
Update: Guys on tenforums helped me out and I was able to fix it! Just needed to recreate the EFI partition which can be done with Windows DiskPart or other 3rd party tools. As a lesson tho: It's better to only have the drive which you want to install the OS (especially Windows) connected while doing it to prevent some bugs like installing system partitions to other drive accidentaly. 
Thank you oldfred for helping me finding the problem!

---

### Post by americk on 2018-12-09
i'm experiencing the same problem, is it possible you could steer me to a link that helped you recreate EFI partition, thanks

---

