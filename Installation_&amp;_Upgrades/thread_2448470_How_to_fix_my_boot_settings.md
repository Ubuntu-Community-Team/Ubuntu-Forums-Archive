---
title: "How to fix my boot settings?"
date: 2020-08-08
forum: Installation &amp; Upgrades
---

### Post by mscofield2 on 2020-08-08
I am in quite a predicament. I have an internal drive that houses Windows 7 and an external drive onto which I installed Ubuntu recently.

I had problems with sound and drivers and the first install went to s*it so I had to reinstall Ubuntu on that drive. Unfortunately for me, the same options weren't there on the second install, so I mistakenly clicked the option to Remove Ubuntu 20.04 and reinstall it. This led to my Windows 7 bootloader to be wiped by grub. Now when I try to boot into my internal drive (Windows 7), I get grub rescue shown up. I reinstalled Ubuntu once again on my external drive with the help of some good people from a discord server. Now my Ubuntu works and I've downloaded a Windows 7 iso file from the internet. 

I've gotten myself a USB stick to use for the Windows 7 recovery boot, so I formatted the stick, set it to FAT32 filesystem and marked it as "Bootable" from Disks. I copied the Windows 7 iso  contents onto the stick afterwards. Unfortunately the boot yields a blinking cursor which doesn't go away. I've checked it out and some other people have posted issues about that too. 

Not only that is my issue though. Opening the bios boot menu yields a non-UEFI and a UEFI version for the USB stick from which to boot from. The UEFI version boots the Ubuntu on my external drive, but the non-UEFI one boots the blinking cursor one. 

There are also 4 external drive boot options that are visible in the image attached to the post.

I do not want to dual boot Ubuntu and Windows 7. I want to run Windows 7 normally when the external drive isn't plugged in and run Ubuntu when it is plugged in.
I've grub-install onto the efi partition of my external drive with commands from this article online: [https://www.58bits.com/blog/2020/02/28/how-create-truly-portable-ubuntu-installation-external-usb-hdd-or-ssd](https://www.58bits.com/blog/2020/02/28/how-create-truly-portable-ubuntu-installation-external-usb-hdd-or-ssd)

Thing is, I have a suspicion my drive is a bit flimsy, check the second image attachment.
There is a 500 MB EFI partition with 33 mb used and another FAT partition with the same stats. Maybe leftover from the 2nd installation (which didn't work btw, I was transported to grub each time I tried to boot, note: not grub rescue like when I would try boot into the windows 7 drive)?

So what I would like to know is how to boot my Windows 7 recovery usb drive and anything else you might tell me from the given information.

---

### Post by pbear42 on 2020-08-08
Easiest way to burn a Windows ISO to flash drive in Linux is mkUSB.  Alternatively, if you have a friend with a Windows machine, Rufus does this very nicely also.

To install mkUSB to your Ubuntu system:
```
[FONT=&amp]sudo[/FONT][FONT=Arial] add-apt-repository ppa:mkusb/ppa
[/FONT][FONT=&amp]sudo[/FONT][FONT=Arial] apt-get update
[/FONT][FONT=&amp]sudo[/FONT][FONT=Arial] apt-get install mkusb usb-pack-efi[/FONT]
```[FONT=Arial]
Create a Windows boot disk is one of the options on the main menu.  By the way, the developer is *sudodus*, moderator emeritus of this Forum (and still active).  You can trust the PPA.

Once booted to Windows, open Power Shell or Command Prompt and run bcdboot C:\Windows ([about]("https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdboot-command-line-options-techref-di")).
 [/FONT]

---

### Post by mscofield2 on 2020-08-08
I tried it, didn't work. Now my USB stick isn't showing in any file manager.

---

### Post by mscofield2 on 2020-08-08
I'm running `sudo dd if=/path/to/Windows.iso of=/dev/sdX bs=1M` now to see if that works

---

### Post by oldfred on 2020-08-08
The dd only works for hybrid DVD/flash drive ISO. No Windows ISO is a hybrid.

If you just installed grub to Windows drive, you should be able to just reinstall a Windows boot loader to Windows internal drive. Best to use Windows repair flash drive, but Boot-Repair can for BIOS installs add syslinux boot loader which is a Windows type boot loader.

But if Windows 7 was UEFI, then only a Windows repair disk will work.
And if your Ubuntu install converted drive from MBR to gpt, bigger issue.
Windows only boots in BIOS mode from MBR and only in UEFI mode from gpt.
Grub only boots working Windows and other installs in same boot mode. 
So if Ubuntu is UEFI on external, it will not be able to boot Windows, if BIOS. But if unplugging drive & then booting in BIOS mode it should work.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

But you really should not be using Windows 7. It is EoL - end of life.
And then is not getting security updates and hackers are looking to get into those EoL systems.

---

### Post by mscofield2 on 2020-08-08
I just checked my partition and it's still marked with MBR partitioning. 

I've tried removing the external drive and booting into the main drive, but the Windows bootloader is no longer there. It was replaced by grub in the 2nd install of ubuntu. And since it finds no device for some reason, it fallbacks to grub rescue

---

