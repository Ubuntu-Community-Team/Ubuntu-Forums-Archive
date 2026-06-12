---
title: "Nvidia Graphics issue(ubuntu freezing) and GRUB2 issue"
date: 2016-01-13
forum: Installation &amp; Upgrades
---

### Post by ashu2 on 2016-01-13
I got a brand new HP Envy Laptop - Quad Core intel processor with 16 GB RAM, 4 GB Graphics card(from Nvidia) and 512 GB SSD. It came installed with Windows 10 Pro(64 Bit). I did partition with Windows tools and then started installing Ubuntu Desktop 14.0.4 LTS Desktop version(along side Windows 10). Installation is fine but I ran into two major issues:
1) **GRUB2 issues.**
[COLOR=#111111][FONT=Ubuntu]Everything went fine but grub2 is not working as expected. Tried boot-repair and here is the link for that:
[/FONT][/COLOR]Boot successfully repaired.
[COLOR=#111111][FONT=Ubuntu]Please write on a paper the following URL: [http://paste.ubuntu.com/14475207/](http://paste.ubuntu.com/14475207/)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]In case you still experience boot problem, indicate this URL to: [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]You can now reboot your computer. Please do not forget to make your BIOS boot on sda (512GB) disk![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The boot files of [The OS now in use - Ubuntu 14.04.3 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If your computer reboots directly into Windows, try to change the boot order in your BIOS. If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader. For example you can boot into Windows, then type the following command in an admin command prompt: bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Also tried executing this line in Windows:[/FONT][/COLOR]
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
[COLOR=#111111][FONT=Ubuntu]It is getting executed also....what could be the issue? I just have to press F9 and then get into grub as of now.
This is fairly new laptop...is it really the case that "The boot files of [The OS now in use - Ubuntu 14.04.3 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk)."? How come BIOS cannot detect the bootable partition? Don't know whether it is true or not? 
[B]2) Ubuntu is freezing may be due to incompatible graphics driver
[/B]As Grub2 is not working fine...i have to use boot-repair and as and when anything lengthy process is running - system freezes...no keyboard or mouse output....tried all the tips provided in that thread but i have to just do a system restart using reset button. What could be the issue?
I have installed the nvidia prime driver also but it hasn't helped either.I can only get into Ubuntu via Windows 10 Pro(restart with shift key and then use ubuntu UEFI).[IMG]https://www.dropbox.com/s/ad4zjn9ckmcci9c/IMG_20160112_210353%20%28Large%29.jpg?dl=0[/IMG]
Looked into other forums and also talked to few friends...everybody saying that install the driver from Nvidia site.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR]

---

### Post by grahammechanical on 2016-01-13
I am confused.

What is the problem with Grub2? You say Grub 2 is not working fine, but in what way? Also, you mention system freezes. It always gets confusing trying to help with more than one problem at a time. So, you are able to load into Ubuntu. So, in what way is Grub not working fine?

---

### Post by Bucky Ball on 2016-01-14
As above. One issue per thread please. Edit out one of the support requests and post it in a new thread with an appropriate title and in the appropriate area. Once you've done that please change the thread title to reflect your support request (Edit Post> Go Advanced).

The lack of paragraphs adds to the confusion. Please use them and use code and quote tags where appropriate to keep the formatting (your outputs run one line into the next). This will help your chances of support as some users will look at a block of unformatted text and move on (I personally have not attempted to trawl through it all). Good luck.

---

### Post by oldfred on 2016-01-14
Ignore Boot-Repair suggestion on /boot partition or far from start of drive issue. That has not applied to any new UEFI based system. It can be an issue on very old BIOS or some BIOS and booting from USB drives a full install.

HP has always been an issue with UEFI boot. They violate UEFI standard and include description as part of UEFI boot. And only description allowed is "Windows". So we have to use a work around.
       **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files efi boot files in efi partition

 **a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu like this:
Boot0013* UEFI OS	HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)

You show this, not sure if BIOS or UEFI, but if BIOS then you need another entry for UEFI, if needed details in link in my signature:
Boot3002* Internal Hard Disk or Solid State Disk	RC

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

Do not install graphics driver from nVidia with a .run file. You will create issues with every kernel update.
Use a ppa if you need the newest driver, but issue may be you are booting with Intel driver?
Can you set which video mode you boot with?

---

