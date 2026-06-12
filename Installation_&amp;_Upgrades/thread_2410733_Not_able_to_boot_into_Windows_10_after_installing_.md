---
title: "Not able to boot into Windows 10 after installing Ubuntu 16.04"
date: 2019-01-19
forum: Installation &amp; Upgrades
---

### Post by dkhelem on 2019-01-19
Hello!

I'm not able to boot into Windows 10 after installing Ubuntu 16.04.
First, I installed Windows 10 on a clean hard drive. Then I made an allocated space using Disk Manager and installed Ubuntu from USB. The security boot was disabled and fast start was turned off before Ubuntu installation. During Ubuntu installation, I was asked whether I wanted to force the EFI installation since the already existing OS was BIOS compatible. To be able to boot the already existing OS, I was offered to not force it.

After Ubuntu was installed, there was no Windows option in the menu, so I tried "sudo update-grub" after which the Windows boot option appeared in the menu, but when I chose it, I was getting a black screen and Windows didn't load. I then tried boot-repair which added a second Windows boot option into the menu but both still do not work. 
Here is the link to the boot info summary provided by boot-repair:
[http://paste.ubuntu.com/p/McKxKwnJ2T/](http://paste.ubuntu.com/p/McKxKwnJ2T/)

Any help will be highly appreciated!
Thank yo in advance!

---

### Post by yancek on 2019-01-19
> but both still do not work. 

Boot repair shows you have Grub installed properly and there are entries for both Ubuntu and windows so what exactly happens when you try to boot windows?  
Is the windows install an upgrade from windows 7?  One thing you might try is changing the active/bootable partition from sda1 to sda2 which you can do with the Ubuntu installer using gparted.

---

### Post by dkhelem on 2019-01-20
Thank you for your respond!
Windows is not an upgrade, I installed Windows 10 on a clean HDD.When I choose Ubuntu from a boot menu, it boots normally. When I choose either of Windows boots (I have two after boot-repair fix: sda1 and sda2), I get a black screen and nothing happens, so I have to do a hard shut down.
Changing bootable partition from sda1 to sda2 didn't help.

---

### Post by yancek on 2019-01-20
> Changing bootable partition from sda1 to sda2 didn't help. 		

No surprise but worth trying.

In your original post, you indicate that you first installed windows 10.  After doing so, were you successfully able to boot and use it prior to installing Ubuntu?   Did you make any changes to windows before installing Ubuntu?

The menuentries for windows point to the correct partition and partition type and have the correct UUID for the specified partition in both cases.  That is generally all that is needed as when a windows entry is selected from the Grub menu, the windows bootloader takes over or at least it should and then you are no longer in Ubuntu or Grub.  Boot repair was designed primarily to repair Linux boot problems but has been able to do some minor repairs to boot windows.  If windows boot files are corrupted, there is nothing boot repair or a Linux system can do.  I don't know what the problem might be so if you need windows, use your windows Installation DVD or Recovery disk or download something from microsoft to repair the windows boot loader.  If you intend to use Ubuntu after, you will need to re-install Grub.

---

### Post by dkhelem on 2019-01-20
Thank you for your reply. After installing Windows, I had no problems  booting into it, and I made no changes except for making unallocated  space for the next Ubuntu installation.

---

### Post by dbergst on 2019-01-20
The pastebin file you provided indicated that boot repair was performed, with the boot loader installed on /dev/sda.  Perhaps you can try this again from your Ubuntu installation by running the following commands:

sudo grub-install /dev/sda
sudo update-grub

---

### Post by oldfred on 2019-01-21
Windows 10 does not make dual boot in BIOS mode easy.
Grub only boots working Windows. And Windows will regularly update to reset or turn on its fast start up or hibernation. And then grub will not boot Windows.
You then have to temporarily reinstall a Windows boot loader using your Windows repair disk or Windows installer's repair console. Fix Windows and then restore grub with Boot-Repair or directly with grub's install commands from Ubuntu live installer.

So you need to reinstall Windows boot loader & fix Windows first.

If UEFI installs, since your hardware is the newer UEFI, then at any time from UEFI boot menu you can directly boot Windows and make repairs. Then from UEFI boot using Ubuntu entry. UEFI is like having two MBR in BIOS mode to make it easy to switch boot.

---

### Post by dkhelem on 2019-01-22
Thank you for you reply @dbergst. 
I tried what you suggested, and, unfortunately, it didn't work.

---

### Post by dkhelem on 2019-01-22
Thank you for your respond @oldfred,

Could you please explain what I should do "to reinstall Windows boot loader & fix Windows first"? Also, I don't really understand what you say about UEFI. Do I need to install it, and if yes, then how? 
Sorry, if my questions look silly, but I am not proficient in those things.

Thank you in advance.

---

### Post by oldfred on 2019-01-22
The disadvantage is that there is no easy conversion to or from UEFI & BIOS. They use different partition types, so usually (especially with Windows) it is a total new install. Or back up all data & start over, if you want to convert to UEFI. How you boot install media UEFI or BIOS mode is then how it installs.

So once you installed Windows in BIOS mode, you need to use Windows tools to repair Windows. You should have Windows repair/recovery flash drive (of your current version) and full backups of Windows at all times.
Then you have to use the command line Windows repair console and fixMBR command. If you do not know Windows repairs:
       [http://www.tenforums.com/](http://www.tenforums.com/) 
            Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    
Then once you have repaired Windows, you can use Boot-Repair to restore grub to MBR to dual boot.
But Windows will keep turning or fast start or occasionally need chkdsk and then grub will not boot Windows. So keep both Windows repair tools & Ubuntu live installer handy.

---

