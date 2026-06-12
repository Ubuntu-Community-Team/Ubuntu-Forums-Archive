---
title: "Installing Grub 2 in Ubuntu 10.10 partition??"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by apanton06 on 2011-01-25
I've seen mixed reviews about installing Grub 2 to the Ubuntu partition while installing Ubuntu 10.10. Some seem to work fine but I've heard there are some problems in doing so.

Would I really face that much of a problem? All I want is to install Ubuntu 10.10 and the Grub to the partition, then I can boot using windows boot loader (and Easy BCD to add Ubuntu) along with Windows 7??

---

### Post by wilee-nilee on 2011-01-25
I would use the grub bootloader to boot in general. all easybcd is doing is pointing the MS bootloader at grub2. 

Grub2 works fine and is a more flexible bootloader then the MS one with easybcd.

The mbr is easy to reload with a MS or the grub2 bootloaders.

Don't believe the paranoia about grub.

---

### Post by kansasnoob on 2011-01-25
The newest versions of Easy BCD support that just fine. As long as you understand where to install grub2 you'll be fine.

OTOH I don't understand why anyone would prefer Easy BCD :D

---

### Post by kansasnoob on 2011-01-25
> **wilee-nilee said:**
> I would use the grub bootloader to boot in general. all easybcd is doing is pointing the MS bootloader at grub2. 

Grub2 works fine and is a more flexible bootloader then the MS one with easybcd.

The mbr is easy to reload with a MS or the grub2 bootloaders.

Don't believe the paranoia about grub.

+1!

Even in the very few corner situations where grub2 doesn't work I'd prefer legacy grub to Easy BCD!

---

### Post by apanton06 on 2011-01-25
> **wilee-nilee said:**
> 

The mbr is easy to reload with a MS or the grub2 bootloaders.

Don't believe the paranoia about grub.

If I decide to uninstall Ubuntu and revert back to Windows 7 as the only OS, how do I go about changing the MBR back to how it was prior to installing GRUB?

---

### Post by wilee-nilee on 2011-01-25
> **apanton06 said:**
> If I decide to uninstall Ubuntu and revert back to Windows 7 as the only OS, how do I go about changing the MBR back to how it was prior to installing GRUB?

With the recovery disc at the command line, the highlighted command.
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by apanton06 on 2011-01-25
I did not receive a W7 installation disc, I only have recovery discs. I do however have a repair disc which runs the system recovery options (including command prompt).
Would I have to use all those commands anyway?

---

### Post by oldfred on 2011-01-25
As wilee-nilee said you only have to run the fixMBR command. The others are if you have other windows issues also.

You can also install a basic windows boot loader from Ubuntu. The windows boot loader just looks for the partition with the boot flag (active partition in windows) and jumps to that partition. Lilo does the same to boot lilo systems but we can just use the MBR part to boot widnows.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by apanton06 on 2011-01-26
Thanks for all your help. I had to use fixmbr before when  I had a problem, I was wondering why wiee-nilee typed all the commands.
I've decided to give both methods a go and see which I prefer.

---

