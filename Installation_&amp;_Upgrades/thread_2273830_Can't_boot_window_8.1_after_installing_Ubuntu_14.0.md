---
title: "Can't boot window 8.1 after installing Ubuntu 14.04.2 LTS"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by bookotl on 2015-04-16
After I installing Ubuntu 14.04.2. There is no boot menu that I can choose which OS I want to boot like installation guide said.
this is URL that Boot Repair gave to me => [http://paste.ubuntu.com/10831240/](http://paste.ubuntu.com/10831240/)

I have no windows 8 DVD anymore.
I tried to fix it already but still can't.

Please help me.

---

### Post by vinh9911176 on 2015-04-16
try sudo update-grub

---

### Post by bookotl on 2015-04-16
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic

this appear after i try.

---

### Post by Dendut on 2015-04-16
Doesn't look like your Windows boot is found.

Use boot-repair and it'll reestablish boot with your Windows 8.
Worst case scenario, you lose grub boot menu and you'll have to erase Ubuntu partition, resize and reinstall.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

1. To use boot-repair, download the iso and use YUMI or another software to create a bootable disk.
2. Run Boot-Repair and follow instructions from the help page above
3. Reboot after it's done it's deed
4. If you can select Windows 8 from Grub boot menu, you're done!

5.  If it boots directly into Windows 8 without the Grub menu, then you'll  need to either fix the grub boot or erase and reinstall Ubuntu

Here's a very useful post:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Good luck!

---

### Post by oldfred on 2015-04-16
Grub2's os-prober looks for both bootmgr & BCD to know which partition has Windows boot files.
Did you have another install of Windows or a separate usually 100MB boot partition?
You are missing the BCD but do have a bootmgr in sda2.

You should always have a current version repairCD or flash drive for every operating system you have installed. And often useful to have other repair tools. You can easily make a Windows repair flash drive from a working Windows.
       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)

Since you are missing BCD you normally would use your Windows repair flash drive and editBCD to fix it.
But you may be able to use third party Windows tools to build a new BCD. I do not recommend EasyBCD for dual booting but it can repair BCDs.
      
 Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

You must also have boot flag on the primary NTFS partition with the boot files or sda2. 
Use gparted from live installer to move boot flag from sda4 to sda2. Grub does not use boot flag, but Windows has to have boot flag to know which partition to boot from, repair, or install into.

---

