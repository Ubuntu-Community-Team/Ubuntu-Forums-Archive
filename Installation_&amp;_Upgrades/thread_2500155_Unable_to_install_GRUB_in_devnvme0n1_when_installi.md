---
title: "Unable to install GRUB in /dev/nvme0n1 when installing Ubuntu 22.04 Dual Boot HP"
date: 2024-08-24
forum: Installation &amp; Upgrades
---

### Post by mbrady06 on 2024-08-24
Hello,
I am fairly new to using Ubuntu and I am  trying to install Ubuntu 22.04 onto my HP Spectre x360. I initially installed it but forgot to check the box to install external drivers, so I think it did not install the driver for my computer's GPU. The screen was just completely black so I tried just restarting it and just installing it again. Since then, I have gotten the error "Failed to install GRUB in /dev/nvme0n1" every single time I have tried installing it. I have secure boot and fast boot both disabled. I have tried changing how I partition the disk in the installer. I have tried with including 500 MB of space for BIOS and for EFI in two separate attempts. In both attempts I have used most of my space partitioned for Ubuntu (about 130 GB) as Ext4 and set the mount point as root (/). Most recently, I have tried setting the boot mode in BIOS to "Legacy Support." I installed boot repair and gotten a report from it but am not really sure what it means. Here is the link to the report: [https://paste.ubuntu.com/p/vqVncMhzy3/](https://paste.ubuntu.com/p/vqVncMhzy3/) 
I appreciate the help.

---

### Post by oldfred on 2024-08-24
Do not mix old BIOS/Legacy/CSM mode & UEFI. That just added to the confusion.
Just always boot in UEFI mode, install in UEFI mode & have system set to default boot in UEFI mode.
How you boot install media, is how it installs & repairs. You booted Boot-Repair in Legacy mode. Reboot in UEFI mode & rerun report & then it gives more details on UEFI install. See line 36.

You show RAID on /dev/nvme1n1. Lines 130 & 137. You typically need to change to AHCI mode, but then for Windows to work have to install AHCI drivers into Windows.  Or is this Intel Optane. Optane now discontinued by Intel. Used only as small fast (SSD) hibernation cache for booting Windows as Windiows booted so slow. 

You show Windows fast startup which sets hibernation flag or hibernation is on. 

You show two ESP - efi system partitions, p1 & p5. Most systems only work with one per drive. Make sure p1 has boot,esp flags in gparted and remove p5. That will require reinstall of grub as it probably was using p5.

HP Pavilion 15t touch (15t cs-200) Post @@ totally remove optane card
[https://ubuntuforums.org/showthread.php?t=2471365](https://ubuntuforums.org/showthread.php?t=2471365)
HP 15 disable Optane
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483) & 
[https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10](https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10) & 
[https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane](https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane)

HP often only boots once. But can be booted directly from UEFI one time boot menu. All other brands work ok, when grub used efibootmgr to change boot order. But HP reverts to Windows. You have to go into HP settings & change boot order in settings.
HP - <kbd>escape</kbd>  + <kbd>F9</kbd> for UEFI boot menu, <kbd>F10</kbd> for UEFI/bios settings
Screenshot of HP's UEFI settings change of boot order
[https://ubuntuforums.org/showthread.php?t=2490924&page=2](https://ubuntuforums.org/showthread.php?t=2490924&page=2)
[https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6](https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6)

---

### Post by mbrady06 on 2024-08-24
I switched back to UEFI and tried to switch the EFI partition on p5 to "do not use this partition" in the Installation Type but it does not look like I successfully switched it. Is there a specific way you recommend removing that partition? Here is the Boot-Repair report: [https://paste.ubuntu.com/p/4wnv7TrX59/](https://paste.ubuntu.com/p/4wnv7TrX59/)

---

### Post by oldfred on 2024-08-24
Both of you current UEFI boot entries use p1, as they have same partuuid. See lines 41 & 43.
So you can use gparted and just delete p5.

But line 137 shows this: > isw_raid_member 

Normally that is Intel RST or Optane and you need to change to AHCI. See above.

---

### Post by mbrady06 on 2024-08-24
I was able to find the option to disable Optane in BIOS and disabled it. I didn't see anything about switching to AHCI. I also went back into windows and expanded my C: drive and then just partitioned it again to remove the extra EFI partition. I booted and still got the same message. This is the current message from boot repair: [https://paste.ubuntu.com/p/7QZY2mjfc8/](https://paste.ubuntu.com/p/7QZY2mjfc8/)

---

### Post by tea for one on 2024-08-24
Line 57 - One OS detected (Ubuntu 22.04)
If you are Dual Booting with Windows 10 (or 11), there should be an entry for Windows.
Is Bitlocker active?

---

### Post by mbrady06 on 2024-08-24
I'm not sure if Bitlocker is active or not. I am still able to boot into Windows 11. I'm not sure why it doesn't show up as an entry at line 57

---

### Post by oldfred on 2024-08-24
Grub only boots working Windows. That also means bitlocker must be off, fast startup or hibernation off, and  chkdsk not required.
If you want to keep bitlocker on, just always boot from UEFI one time boot menu, not grub.

---

### Post by mbrady06 on 2024-08-24
I would be okay with booting from UEFI, but Ubuntu doesn&#8217;t even show in the boot options.

---

### Post by oldfred on 2024-08-24
Run a new copy of Boot-Repair report & post link.
When in UEFI mode, it shows more UEFI boot info that your previous report is missing.

---

### Post by mbrady06 on 2024-08-25
I ended up turning off Bitlocker and this is the current boot repair report: [https://paste.ubuntu.com/p/54s7pJKxX3/](https://paste.ubuntu.com/p/54s7pJKxX3/) 
I think I would like to turn Bitlocker back on if possible though

---

### Post by yancek on 2024-08-25
Beginning at line 5 of boot repair, it indicates you tried to do a Legacy install of the Ubuntu Grub and failed as you are using a GPT drive (see line 104) which requires a 2MB unformatted partition on which to put the core.img file.  If you insist on doing a Legacy install of Ubuntu, that is needed.  The problem is that if yuo do that you will not be able to boot windows from the same drive with Grub.  

If you look at lines 10-23 of boot repair you will see the entire contents of the EFI partition which include only manufacturer (HP) and windows files. This is why you don't see Ubuntu in the BIOS boot options, because you didn't install properly.   Booting and installing Ubuntu in UEFI mode would have been the simplest solution.  You have Ubuntu on partition 5 already so just install Grub EFI.

I don't know BitLocker or what options you have with that.

---

### Post by tea for one on 2024-08-25
> **mbrady06 said:**
> I ended up turning off Bitlocker and this is the current boot repair report: [https://paste.ubuntu.com/p/54s7pJKxX3/](https://paste.ubuntu.com/p/54s7pJKxX3/) 
I think I would like to turn Bitlocker back on if possible though
As indicated by yancek, run the recommended boot-repair (details line 237 etc.)

You had, at least, three problems at the beginning:-
Bitlocker active
Intel Optane obstruction
Installation of Ubuntu in Legacy mode

Leave Bitlocker disabled for the moment until you are happy that you can dual boot seamlessly.

If the boot-repair fails, run another boot-repair report.

---

### Post by mbrady06 on 2024-08-25
I was able to run Boot repair and get GRUB installed. Thank you for the help

---

### Post by oldfred on 2024-08-25
HP requires you to go into system settings & change boot order there.
Every other brand works with efibootmgr which grub uses to change boot order.

May be sub-menu of UEFI boot settings.
Screenshot of HP's UEFI settings change of boot order
[https://ubuntuforums.org/showthread.php?t=2490924&page=2](https://ubuntuforums.org/showthread.php?t=2490924&page=2)
[https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6](https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6)

HP Spectre x360 13-4102dx 24.04 no issues install
[https://ubuntuforums.org/showthread.php?t=2499399](https://ubuntuforums.org/showthread.php?t=2499399)

Lots of threads on x360
HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume) & 
[https://askubuntu.com/questions/1345338/common-failed-to-install-grub](https://askubuntu.com/questions/1345338/common-failed-to-install-grub)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086) & 
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)
HP Spectre x360 15t  Optane issue
[https://ubuntuforums.org/showthread.php?t=2474790](https://ubuntuforums.org/showthread.php?t=2474790) & 
[https://chanon.info/install-ubuntu-22.04-on-hp-envy-x360/](https://chanon.info/install-ubuntu-22.04-on-hp-envy-x360/)

---

