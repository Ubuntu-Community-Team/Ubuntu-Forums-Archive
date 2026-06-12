---
title: "Dual OS Infinite Reboot Loop Can't get to GRUB"
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by jchan91 on 2013-03-23
Hi,

I have my machine setup to dual boot Windows 7 and Ubuntu 12.04 via grub. However, after I did a Windows Update today, it went straight to grub rescue. I messed with "set root" a little, and tried to reboot again. It then got to grub and I was able to boot Windows normally. Then I tried to reboot again, and now, it doesn't even go to grub or grub rescue. It just continuously reboots.

I attempted to purge and re-install grub via boot-repair from live-USB, but nothing has changed. The following is the bootinfoscript:

[B][[COLOR=#1155CC][FONT=Arial]http://paste.ubuntu.com/5641963/[/FONT][/COLOR]]("http://paste.ubuntu.com/5641963/")

[/B]I have a weak understanding of bootloaders, so any suggestions would be greatly appreciated! I have no idea which direction to investigate next.

Please help! I urgently need the laptop this week. Thank you in advance!



_Extra history that may or may not help:_
After I first set up the dual boot, I had problems going from Windows to Ubuntu, not the other way around though. When I would try to boot into Linux, I would get a:
[COLOR=#000000]
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[/COLOR]
I would then hard restart, and grub would load again, and then I would be able to boot into linux normally. After several months, the same procedure would cause a different error. Instead of a Kernel panic, I got:
[COLOR=#000000][I]
error: invalid arch independent ELF magic

[/I][/COLOR]Again, I would do a hard reset, and then I would be able to boot normally, so I ignored this problem for a while until now.

---

### Post by oldfred on 2013-03-24
Not sure if you just reinstalled grub to MBR or did a full uninstall and reinstall of all of grub.

 
 error: invalid arch independent ELF magic

 Often version of grub in MBR is not same as install. 
Use same version to reinstall or chroot and fully uninstall & reinstall.

Boot Repair has a helper function to chroot, fully uninstall & reinstall grub.

Is this system an UltraBook? That has the small SSD with Intel SRT for caching Windows. That may be part of your issue, but I have seen users with that and dual boot. Since Intel standard every vendor is essentially the same.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

---

### Post by jchan91 on 2013-03-26
Thank you very much for the resources and help! I'll look them over first. I believe I did a purge and install on sda5 (which were the only options I was given in Boot Repair). And yes, this system is a Sony Vaio SVT13112FXS Ultrabook with a 32GB SSD on sdb.

---

### Post by oldfred on 2013-03-26
If SRT is on and RAID meta data still on drive, then grub does not seem to install correctly. 
Others have reported they could turn it off, then install grub and turn it back on. 
Those that use Windows less & Ubuntu more, just turn it off and use the SSD for / (root) with data on spinning disk.

---

### Post by jchan91 on 2013-03-26
> [COLOR=#000000]error: invalid arch independent ELF magic[/COLOR]

[COLOR=#000000]Often version of grub in MBR is not same as install. [/COLOR]
[COLOR=#000000]Use same version to reinstall or chroot and fully uninstall & reinstall.[/COLOR]

My boot info script says that grub 1.99 is on MBR of sda, and points to ( , msdos5) for /boot/grub. On sda5, I see grub.cfg, and was unable to find any menu.lst, so isn't that an indication that the MBR and linux partition are running grub2? Could grub be corrupted on one or both of these places, despite the boot info script reporting info about them? How reliable is the boot info script?

Also on the side, why is my partition labelled as msdos5 as opposed to just 5?

> [COLOR=#000000]If SRT is on and RAID meta data still on drive, then grub does not seem to install correctly. [/COLOR]
[COLOR=#000000]Others have reported they could turn it off, then install grub and turn it back on. [/COLOR]

My understanding is that these people are removing RAID metadata because when they are trying to install Ubuntu, the installer doesn't detect the HDD. But I already have 12.04 installed on sda5 (my SSD is sdb). So shouldn't my concern be trying to get grub2 on sda's MBR, then have it point to grub2 on sda5, which will then take care of finding the windows bootloader?

> [COLOR=#000000]Those that use Windows less & Ubuntu more, just turn it off and use the SSD for / (root) with data on spinning disk.[/COLOR]

I use both quite equally, so I'm hoping to keep RST, and SRT if possible too.

Thanks for all the help again, and the quick responses!

[U]
Secondary Questions:
[/U]
I am trying to debug where this is going wrong. When I boot, I know I get through BIOS first, before it reboots again (if I don't have live USB plugged in). So does that mean I'm still in stage 1 of grub2? Or could I possibly have reached stage 2? What stage have I reached if I make it to grub rescue? What about grub menu?

---

### Post by oldfred on 2013-03-26
You  have grub2. Unless you have 0.97 that is grub legacy with menu.lst. Grub2 with Ubuntu started at 1.97, and only 12.10 has the newest grub2 version 2. With 12.04 you still have 1.99.
And with UEFI it installs efi versions of grub that are somewhat different.

The issue seems to be with RAID on, grub refuses to install. Not sure you have to remove meta-data anymore or not. Ubuntu used to not install at all with Desktop installs to RAID, only with the Alternative installer. But with 12.10 they have eliminated the alternative installer and will eventually include RAID. I think the installer has been updated, but grub has not been totally updated yet to work with RAID. Normally with RAID, grub is installed to the RAID not MBR or with UEFI, grub2 is actually installs its boot loader to the efi partition, not anywhere else.

If you have msdos partitions, you must not have the new UEFI versions. With UEFI, you have gpt partitions and to keep them straight on which driver to use, it now says msdos5 or gpt5 for example.

I think you only have to turn off Intel SRT, install grub with Boot-Repair and then turn it back on.

       Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by jchan91 on 2013-03-26
> I think you only have to turn off Intel SRT, install grub with Boot-Repair and then turn it back on.

For my Sony Vaio T, there does not appear to be an option  to change the "SATA option" as described by the Dell user. And since I  can't boot into Windows, I can't disable it from there either. Could I  just use dmraid on sda to disable SRT? Is this the same as disabling  RAID from BIOS?

If I do use dmraid and erase the metadata in sda,  does that mean I will lose RST/SRT tech when I am on Windows? Or will  turning off and on SRT in Windows restore that metadata?

---

### Post by oldfred on 2013-03-26
I gathered from the threads posted above that they turned it off, ran the commands to remove RAID meta-data, but were able to turn it back on and it worked.  But I have not done it.

---

### Post by jchan91 on 2013-03-28
> Normally with RAID, grub is installed to the RAID not MBR or with UEFI,  grub2 is actually installs its boot loader to the efi partition, not  anywhere else.

What did you mean by grub is installed to RAID, not MBR? I thought RAID was a way of redundantly storing data on multiple disks, whereas the MBR is a piece of code+data that is supposed to be stored in the first sector of the first drive. Doesn't grub code belong in the MBR so that it can find the linux VBR? Shouldn't the concept of RAID (how data is stored) be abstracted from where data is stored?

Forgive me if I am completely misunderstanding how bootloaders and hard disks work. Please redirect me to search terms or articles that would clarify these concepts.

---

### Post by jchan91 on 2013-03-31
Update: dmraid also does not detect that I have a RAID setup on sda, only on sdb (the SSD). There is also no way for the Sony Vaio T to reconfigure RAID from BIOS.

---

### Post by oldfred on 2013-03-31
Is BIOS in RAID, LBA, IDE or AHCI for hard drive access? Not sure with Intel SRT but I think it uses RAID. Normally we now use AHCI.

I think you can remove meta-data from sdb & it will just recreate it when you turn it back on in Windows.

---

