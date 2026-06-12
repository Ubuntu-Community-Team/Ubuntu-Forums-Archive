---
title: "Kubuntu installer stuck after &quot;Updates and other software&quot;"
date: 2021-11-01
forum: Installation &amp; Upgrades
---

### Post by davice on 2021-11-01
Hi,


I'm trying to install Kubuntu 21.10 on my current pc alongside with Windows 10 which is already installed. As soon as I choose the options in the section Updates and other software and click continue, a label appears saying that it's preparing ubuntu drivers. After a few seconds, it disappears and it gets stuck.


I've already tried disabling download updates while installing Kubuntu and disabling the option to install third-party software, but it still gets stuck there. If I force a shutdown, it takes a while because of the "ntfsresize", so I think it can't analyze the disks for some reason. I've also already tried changing the USB port and using another pendrive.


I've read on the internet that the default ubuntu installer gets stuck if windows is installed, and that mounting and unmounting the windows partition a few times fixes the glitch, but neither the KDE partition manager nor GParted let me do it, the option is greyed out.


I have 3 drives in total in my system, with a Core i5 4440 and a GTX 960, and I want to install Kubuntu on a drive where windows is not installed.


I hope you can help me out, if you need more infos please ask me. Thanks in advance.

---

### Post by coffeecat on 2021-11-01
Kubuntu is an official flavour of Ubuntu, so this is OK in one of the main Ubuntu and official flavours sections. *Thread moved to **Installation & Upgrades**.*

---

### Post by grahammechanical on 2021-11-01
Have you turned off Windows fast startup? It is a form of hibernation and it prevents Linux from reading the drive. It might be best anyway to disconnect the Windows drive as you are wanting to install Kubuntu on a second drive.

If the installation completes and you can load Kubuntu, then reconnect the Windows Drive and load into Kubuntu and run

```
sudo update-grub
```

That should put Windows in the Grub boot menu.

Regards

---

### Post by tea for one on 2021-11-01
> **grahammechanical said:**
> It might be best anyway to disconnect the Windows drive as you are wanting to install Kubuntu on a second drive.

Yes, this is a good idea.
If you only have the target drive accessible, human error is virtually eliminated.
Dual booting is far easier to manage when each OS is on a separate drive.
Make sure that you install Kubuntu in UEFI mode with GPT (partition table)

---

### Post by Shibblet on 2021-11-03
I am currently running Kubuntu 21.10

In order to install it correctly, I booted from the USB, and went into "Try Kubuntu"

After booting to a desktop, I opened up my terminal and ran "sudo apt-get update && sudo apt-get upgrade"

Then, I ran the installer on the desktop.  Everything worked great!

---

### Post by oldfred on 2021-11-03
If installing to a separate drive, it should not be doing any Windows resize.
Or is Windows on other drive not in UEFI boot mode, and now installer wants an ESP on that drive? It used to just fail as grub would not install to first drive in UEFI mode if first drive does not have an ESP - efi system partition?

Review this bug for any install to a second drive whether internal or external.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

If UEFI system and UEFI install of Windows (which it should be if UEFI hardware), you must partition in advance and have an ESP on your Ubuntu drive.
UEFI/gpt partitioning in Advance, new versions use swap file so swap partition optional:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 

Minimum partitions should be ESP & / (root), if larger drive then smaller / & separate /home suggested.
For larger drive, I typically do not fully partition a drive initially.
Advanced users suggest LVM which gives lots of flexibility, but requires bit more knowledge of Linux.

---

