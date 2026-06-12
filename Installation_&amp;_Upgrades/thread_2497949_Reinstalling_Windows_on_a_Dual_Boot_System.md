---
title: "Reinstalling Windows on a Dual Boot System"
date: 2024-05-23
forum: Installation &amp; Upgrades
---

### Post by faust99 on 2024-05-23
I have to reinstall Windows 11 on my dual boot system, on which I also have Ubuntu 23.10. What will happen to the boot loader in this case? Will I be able to boot into Ubuntu if I reinstall Windows? Please advise.

---

### Post by yancek on 2024-05-23
You need to check/know if both are UEFI installs.  If you boot the computer, immediately hit the proper key to access the BIOS and check for Boot Options.  On an EFI system, you should see options for both windows and ubuntu.  If you have a GPT drive then microsoft requires you use EFI.  As long as you select the Custom option while installing windows, you will be able to select the drive and partition on which you wish to install it.  Ubuntu will have a different filesystem type than windows so you can tell them apart that way.  Also, windows doesn't give drive letters to Linux partitions.  When you install windows, it will likely put itself first in boot order and boot itself so you will need to go into the BIOS settings and change that to Ubuntu.  To add windows to the Grub boot menu, you will need to boot into Ubuntu and run sudo update-grub.

Are you booting both from the Ubuntu Grub?
Are windows and Ubuntu on the same physical drive?
Do you know if you have an EFI install?  If you do, you will have an EFI partition with a vfat filesystem which you should be able to see from Ubuntu (command:  ls /boot/efi/EFI) or from windows in Disk Management.l

---

### Post by faust99 on 2024-05-23
Thanks for your response. I do have both Windows (broken) and Ubuntu in my boot options. I upgraded my BIOS, in the false hope that it would allow me to boot into Windows Safe Mode, and since then, when the system boots it goes straight into Windows, bypassing the Grub boot menu. As such, to boot into Ubuntu, I need to go into the BIOS and choose Ubuntu, after which the Grub boot menu comes up.

I have Windows and Ubuntu on the same physical drive. The output of ls /boot/efi/EFI is: Boot  Microsoft  ubuntu

---

### Post by MAFoElffen on 2024-05-23
What brand of Computer/Model? That would tell us which hot-key to press during the boot, to get to the UEFI Boot Menu...

Once you get Ubuntu booted, then others here can talk you through resetting the order in the UEFI boot order with efibootmgr. That will get you back to using Grub2 as the boot manager.

---

### Post by tea for one on 2024-05-24
> **faust99 said:**
>  I do have both Windows (broken)and Ubuntu in my boot options. 
After you have re-installed/repaired Windows 11, I would expect that the Windows Boot manager will take precedence over Grub
> **faust99 said:**
> I need to go into the BIOS and choose Ubuntu, after which the Grub boot menu comes up.
After you have established that your Windows 11 OS is working OK, boot into Ubuntu via UEFI boot menu and let's see if Grub can be set to boot both Windows and Ubuntu.
Grub will only accept a Windows entry if [COLOR="#0000FF"]Windows is working[/COLOR] normally.
You'll need to identify your disk - couple of examples below:-
```
sudo grub-install /dev/sda # assuming your disk is sda

sudo grub-install /dev/nvme0n1 # assuming your disk is nvme0n1
```
```
sudo update-grub

```
If this fails, then you'll need to re-install Grub via a live session.
Try the above first and report the result

---

### Post by faust99 on 2024-05-25
Thank you. I've somehow managed to set up Grub so that it gives me all the boot options, as before, even though my ******* installation is still broken. The problem is I can't seem to reinstall Windows 11; I've read somewhere in passing that it's problematic to install it when there are other operating systems in place. I've tried creating USB lived discs using Unetbootin, Balena Etcher as well as Ventoy (both from the Windows 11 iso as well as Media Creation Tool), but each has resulted in various errors. Will I have to wipe my current Ubuntu installation in order to do a fresh install of Windows 11?

---

### Post by tea for one on 2024-05-25
> **faust99 said:**
> but each has resulted in various errors.
Difficult to answer without knowing what the errors are.
> **faust99 said:**
> Will I have to wipe my current Ubuntu installation in order to do a fresh install of Windows 11?
Depends on the unknown errors

---

### Post by ubfan1 on 2024-05-25
Also which Windows 11 feature set are you trying to install?  The 22h2 I think installed from the USB easily, but the 23h2 needed some registry tweaking to get the installer to accept the underconfigured, old machine as acceptable. The feature sets get EOLed after 2 years, so a later one is better if you can get it to work.  I've used the Media Creation Tool to download and write a USB successfully, and also by making boot USB formatting it FAT, copying all the files from the ISO except the too big one install.wim (?).  Use wimsplit from the wimtools package to split that file up into two files with extension .wms that the installer will know how to combine.

---

### Post by coffeecat on 2024-05-26
> **faust99 said:**
> even though my ******* installation is still broken.

Was that a profane word or a disrespectful misspelling of "Windows", either of which could have triggered the forum censor? (Which is there to prevent inadvertent contravention of the forum [Code of Conduct](https://ubuntuforums.org/misc.php?do=showrules).)

You might find the "Preview Post" button useful before actually submitting your post. I certainly find it useful, although I'm not usually in the habit of triggering the forum censor. :wink:

---

