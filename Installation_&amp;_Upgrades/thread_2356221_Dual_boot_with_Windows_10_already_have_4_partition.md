---
title: "Dual boot with Windows 10: already have 4 partitions: unsure which to delete"
date: 2017-03-21
forum: Installation &amp; Upgrades
---

### Post by dabs17 on 2017-03-21
I have trying to figure out how to setup a dual boot alongside Windows 10 on my primary laptop. This is my first time installing any OS other than Windows. I have tried reading many previous posts, but I am still unsure about the problems with partitioning and UEFI. 

My Windows 10 installation already has 4 partitions (see Disk Management screenshot). On a number of other posts, people have mentioned deleting the Recovery partition to create room for Ubuntu, but I am not sure which one of my 4 partitions is the Recovery one. Because of this (I think) I don't see the Default option to install Ubuntu as Dual boot when trying through the bootable USB. The descriptions and sizes of these partitions are completely different when I tried to go into the advanced options of Ubuntu installer. So I am not sure what my path forward is.

I have a Dell Inspiron 3542 laptop running Windows 10 Home OS. Happy to provide any additional details necessary.

Any help? Pretty please!

---

### Post by Bucky Ball on 2017-03-21
Welcome. You have a heap of free space available on 'D'. Why not shrink that with Windows disk management tools (defrag the partition a number of times first) and that will leave you free space for your Ubuntu install. 

If you are in UEFI it doesn't matter how many partitions you have (theoretically). It does not have the four partition limit of a legacy install. 

At least, you are going to need a / partition and a 2Gb /swap partition for Ubuntu. Ubuntu (which installs to the '/' partition) will only need about 20-25Gb (not even that depending, but that's safe) and you can link to the existing data in your other NTFS data partitions from Ubuntu and Windows. Best to avoid creating a whole bunch of personal data in two OSs. Remember, Windows can not access data on a Linux EXT* partition (and Ubuntu must be installed on one), while Ubuntu can access NTFS partitions. Therefore, it is common practice to create (or use an existing) an NTFS partition as a 'shared' partition for both OSs.

Hope that gets you some of the way. Any questions, just ask and good luck. ;)

PS: Don't know where you read it, but never a good idea to kill the recovery partition. If you ever decide you need the machine back to the factory 'default' (for instance, if you want to sell it) with Windows installed and nothing else, then the recovery partition is your friend. If you have Win on a disk and ready to install or if you have run the recovery to create recovery disks already (I generally create two copies) and you can readily install Win again if you want to, then go ahead. If you don't care about ever needing to get the machine back to its 'vanilla' factory state, then kill recovery. Your choice. ;)

PPS: If your Win is in UEFI mode, why are you trying to install Ubuntu in legacy??? (Second pic.) It MUST be installed in the same mode as Windows. And you MUST have free space to install to. If you let Ubuntu do it, you run the risk of wiping everything on the drive and you will have Ubuntu only. DO NOT choose erase disk (third pic). You want 'Something Else'. 

There is an anomaly in pic 4. Gparted is not picking up the correct details for your partitions. Try booting the installer in UEFI mode and 'Try Ubuntu'. Might see things differently. Either way, /dev/sda4 equates to Win 'D' drive (partition) and is the one you want to shrink *_with Windows tools_*, NOT with Gparted. :)

---

### Post by dabs17 on 2017-03-21
I can shrink D: by 100 Gb. Should I create a new volume out of that or leave it as Unallocated?

When you say a "/ partition", does that mean /dev/sda, the 1st option I see in Ubuntu installer?

For the 'shared' partition, do I need to do anything special during the installation, or would that be automatic?

Sorry if the questions are illogical, I have never done this before, and it would be a major pain if something happened to the Windows installation.

---

### Post by Bucky Ball on 2017-03-21
Have edited my post. Have another read. In Ubuntu, sda is the first drive, sda1 is the first partition on the first drive. Windows is confusing in that it calls partitions drives. This is incorrect. :)

---

### Post by dabs17 on 2017-03-21
I freed up space on D using Disk Management, leaving the remaining ~100gb as unallocated space. I tried to install Ubuntu as I was till now, and the sizes of the different partitions didn't change at all (/dev/sda4 was the same size. Shouldn't it be different if I shrunk the drive?)

 With regards to UEFI/Legacy, I am not selecting any option to install Ubuntu in legacy. I made a bootableUSB as per instructions on the website, and I select USB Storage Device from the boot options to run the Ubuntu bootable USB. Am I doing something wrong?

---

### Post by Bucky Ball on 2017-03-21
When you boot to a live session (Try Ubuntu), and launch Gparted, do you see unallocated space there? Does that show things as expected?

In any case, try following the [instructions for the 'Something Else' install]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation") which is the second answer on the link, from memory (with pics). Have a good read and look through so you understand what you're about to do.

Also, have a [look here under the heading 'Install Ubuntu']("https://turbofuture.com/computers/Dual-Boot-Ubuntu-1604-LTS-and-Windows-10") down the page. The only difference is the absence of a 2Gb /swap partition. If in doubt, add one. I always use one, but others don't. You could research [the ongoing debate]("https://duckduckgo.com/?q=swap+necessary&t=ha&ia=web") and make your decision from there. :)

Just to confirm: You are installing a supported Ubuntu? 16.04 LTS (supported until 2021), 16.10 (til July)? If not, please do. You are using the 64bit desktop ISO for a 64bit machine?

PS: You wrote in your first post:

> **dabs17 said:**
> ... I am still unsure about the problems with partitioning and UEFI. 

You need to boot the Ubuntu install media in UEFI mode. You set that in the BIOS by selecting the boot device with [EFI] next to it as the first boot device.

---

### Post by Impavidus on 2017-03-21
Your uefi is in legacy mode and there's no efi partition, so definitely mbr partitioning/bios mode. This means you have a 4 primary partition limit. Your main problem however is that Windows uses dynamic partitions. Linux doesn't know how to deal with Windows dynamic partition. That's why the Ubuntu installer and Windows disk management give completely different layouts of the partitions on your hard drive. When you use Linux tools to change anything on your partitions, you'll break Windows. You have to get rid of those dynamic partitions and there's (AFAIK) no official way to do so. You may be able to use some third party tools.

---

### Post by dabs17 on 2017-03-21
[QUOTE=Bucky Ball;13623185]When you boot to a live session (Try Ubuntu), and launch Gparted, do you see unallocated space there? Does that show things as expected?

I tried that with gparted (see attached image) and basically the entire D: + unallocated space (created after shrinking D: using Disk Management) shows up as unallocated. Don't know what to make of that. It seems Ubuntu is unable to differentiate between the D: and unallocated space I am trying to create for installing Ubuntu.

---

### Post by Bucky Ball on 2017-03-21
[Post #7]("https://ubuntuforums.org/showthread.php?t=2356221&p=13623254&viewfull=1#post13623254") from Impavidus may shed more light. Have a read.

---

### Post by dabs17 on 2017-03-21
I think my Win is running Legacy BIOS, even though it is UEFI capable. When I try "System Summary", it says "Legacy" under "BIOS mode".

Yes, I'm trying with 16.04 LTS. I have the 64bit ISO.

> **Bucky Ball said:**
> Just to confirm: You are installing a supported Ubuntu? 16.04 LTS (supported until 2021), 16.10 (til July)? If not, please do. You are using the 64bit desktop ISO for a 64bit machine?
.

Thanks for the reply. This is so annoying. I am guessing I have no options besides reinstalling Win10 from scratch?

Thanks for all your prompt replies. I guess I will have to try installing a VM and go that route.

---

### Post by oldfred on 2017-03-21
You can use some third party tools to convert dynamic back to basic if you only have 4 partitions.
 [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html) 

Then you have to convert one primary to be the extended. Most have a small vendor utilities partition that they can backup and delete.
You can have as many logical partitions inside the extended partition as you want.
You may be able to use fixparts to change a partition to logical. Do not do the change to gpt, as that will break Windows in BIOS boot mode.

 [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/) 


If you want UEFI, you have to totally reinstall Windows and boot its installer in UEFI mode to install in UEFI boot mode.
Windows in UEFI boot mode, must use gpt partitioning.
      
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

---

### Post by ubfan1 on 2017-03-21
Well, as mentioned there are third party tools that offer to convert dynamic to basic without data loss (Google convert windows dynamic disk to basic) but who knows how they'll work.  If you're going to reinstall anyway, you might try one, if free.  The "Microsoft" way seems to be: backup, delete the dynamic partitions, make basic partitions, restore.

---

