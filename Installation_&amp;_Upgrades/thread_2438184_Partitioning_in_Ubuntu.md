---
title: "Partitioning in Ubuntu"
date: 2020-03-07
forum: Installation &amp; Upgrades
---

### Post by mohammadzf on 2020-03-07
Hello there,


I have no experience installing Ubuntu and need some help.


My laptop has 128GB SSD and 1T HDD with 8GB Ram. (Lenovo z500)


Do I want to know if I should use Erase Disk and install Ubuntu or Other options (manual partitioning) ?


My goal is to have the best performance What is your suggestion to install on these 2 hard drives?

Best Regards.

---

### Post by Impavidus on 2020-03-07
You've got two hard drives. The installer doesn't know how you want to use them, so best to use manual partitioning. The option to "erase disk and install Ubuntu" works fine if you've got only one hard drive and don't really know what to do (it will create one big partition for everything), but for more advanced cases it's better to do things manually.

128GB is far more than you need for your OS. I would use the SSD for my main system, a spare system and a /home partition with most of my documents and keep the HDD for media files. But only you know how you're going to use your system.

---

### Post by oldfred on 2020-03-07
Do not know if yours is new enough for this to apply, but good to make sure you have latest UEFI anyway.
UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)

Are you planning on dual booting with Windows?
If not be sure to back up your Windows install. We have many users who come back after erasing Windows and later find one program or game that only runs on Windows and want to reinstall.

You have nVidia, so will need nomodeset to boot install media. Normally needed on first boot after install, but newest versions let you install proprietary nVidia driver as part of install, so nomodeset not needed once installed.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Generation older had a bug of some sorts.
[https://askubuntu.com/questions/1178883/ubuntu-18-04-requires-multiple-attempts-to-boot](https://askubuntu.com/questions/1178883/ubuntu-18-04-requires-multiple-attempts-to-boot)

---

