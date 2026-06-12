---
title: "Ubuntu 18.04 not booting after Uninstalling Windows 10 from Dual Boot"
date: 2019-12-31
forum: Installation &amp; Upgrades
---

### Post by azhar.basit on 2019-12-31
[COLOR=#242729][FONT=Arial]So I have an Acer Aspire E5, laptop which came with Windows 10.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I installed Ubuntu 18 on it as Dual boot.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now running out of diskspace I tried to remove Windows 10. However now I am unable to boot into Ubuntu.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Summary of what I did.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Used Ubuntu USB Live then,[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Used Gparted / OSuninstaller to remove Windows 10. Deleted the Windows 10 partition and also EFI/boot partitions after having lots of problems. I used boot-repair to repair my boot. The paste-bin of log with an error "Unknown Boot-loader" is here:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][boot-repair output]("http://paste.ubuntu.com/p/HRFMdqZ4MQ/")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Finally my partitions looks like this as seen from GParted on live USB:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][GParted Image]("https://i.stack.imgur.com/HavjJ.jpg")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now when I boot I get the grub options:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][grub screen shot]("https://i.stack.imgur.com/HOIur.jpg")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]However at the end I get the following and am unable to boot:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]"You are in emergency mode.."[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][Unable to boot , emergency mode]("https://i.stack.imgur.com/XlyNI.jpg")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The good thing is that all my data is still there, which I can see from a live Ubuntu USB which mounts the laptop drive.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So I do not Windows but maybe removing the EFI/boot partition caused this issue. Also the boot-repair wants me to boot with UEFI mode (and not legacy). So can this be fixed? or do I need to buy a new drive, install Ubuntu on it and move my data?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks![/FONT][/COLOR]

---

### Post by CatKiller on 2019-12-31
> **azhar.basit said:**
> Deleted the Windows 10 partition and also EFI/boot partitions 

You definitely needed to keep your EFI partition: that's where your bootloader lived. You could have removed the Windows bootloader from your ESP. 

You'll need to boot in UEFI mode and recreate your ESP with the information needed to find your Ubuntu install. I've no experience with boot repair, but oldfred may well be along to help you through it or you could check his posts for information on the process. He is experienced with that kind of thing.

---

### Post by yancek on 2019-12-31
I'm not familiar with "[COLOR=#242729][FONT=Arial]OSuninstaller".  The standard method to accomplish your initial goal would be to simply format the unmounted windows partitions w/gparted from Ubuntu with a Linux filesystem.  I see you successfully removed the windows EFI files from the EFI partition.

You see at the top of the report that there is no boot code in the MBR of either drive.  Scroll down to sda2 and you see BIOS boot partition.  sda2 currently is useless as that is only used when you have a Linux install on a GPT drive and you have a Legacy install.  Legacy install means boot code in the MBR.  First thing, if not already disabled, disable Legacy/CSM boot in the BIOS firmware so that the machine boots EFI.  You have Ubuntu efi files on the efi partition and boot repair indicates you need to point to a specific file to boot Ubuntu  ([/FONT][/COLOR]Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!).  On some computers, there will be an option to "Boot from EFI file" which you should select and search for that specific file to boot.  If you don't have that option, you will need to search the BIOS to find anolther way to boot it.  If you look at the efibootmgr output or run it yourself, the option you want is Boot 0000[COLOR=#242729][FONT=Arial][/FONT][/COLOR][COLOR=#242729][FONT=Arial].  You might be able to use efibootmgr from the Ubuntu install media though I'm not sure it is installed.  Have you tried the other options seen on the boot menu and were the results the same?     
[/FONT][/COLOR]

---

