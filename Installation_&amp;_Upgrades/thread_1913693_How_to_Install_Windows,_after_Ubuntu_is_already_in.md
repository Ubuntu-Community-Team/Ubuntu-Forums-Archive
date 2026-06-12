---
title: "How to Install Windows, after Ubuntu is already installed"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by BotoxRehab on 2012-01-23
Hi there, so I have a bit of a problem.

I have a netbook with no CD/DVD drive so everything I have to do will be on a bootable USB Flash Drive (USBHDD). I am very knowledgable with computers and for the most part know what I'm doing.

[COLOR="Magenta"]Problem 1[/COLOR]: Windows 7 had a virus so I wiped my computer and did a fresh install of Ubuntu's latest release via USBHDD.

[COLOR="Magenta"]Problem 2[/COLOR]: I now only have Ubuntu on my system and I want Windows back. (I don't care if it is dual boot or not at this point)

I have tried UNetbootin and even got my friend to make a bootable windows USBHDD, it for some reason will not register with my system now that Ubuntu is installed. I have changed boot sequence and ladida... I know what I'm doing with that aspect. But what I don't understand is why

A: It's not recognizing my Windows Bootable USBHDD flash
B: This only started after I installed Ubuntu

I really want Windows back and am willing to do anything to get it back. Can someone help me by answering or even linking me to somewheres that will be of great assistance?

I have tried google searches, this is kind of a last resort for me.

Hope to hear from someone soon. xo

---

### Post by carl4926 on 2012-01-23
Do you have a windows DVD
I don't mean recovery disks. I mean a proper windows install DVD?

---

### Post by BotoxRehab on 2012-01-23
I used PowerISO to burn the .iso file to the drive from the disk. There is an option to copy my Windows DVD to the Flash drive and thats what I did.

---

### Post by carl4926 on 2012-01-23
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

---

### Post by carl4926 on 2012-01-23
> **carl4926 said:**
> [http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

But you may need a working windows PC to actually do some of that.
It does work because I have used it. I prepared the USB on a windows PC though

---

### Post by BotoxRehab on 2012-01-23
what size flash drive did you use?

---

### Post by carl4926 on 2012-01-23
8gb            .

---

### Post by oldfred on 2012-01-24
Windows cannot see the Linux partitions. It has to have a primary sda1 thru sda4 NTFS formated partition with the boot flag or active partition.

Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")

After you install Windows you will have to reinstall the grub2 boot loader to the MBR if you want to dual boot. Then run this to find the Windows install to let you dual boot.
sudo update-grub

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

