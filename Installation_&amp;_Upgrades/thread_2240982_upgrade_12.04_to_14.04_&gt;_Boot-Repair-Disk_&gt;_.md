---
title: "upgrade 12.04 to 14.04 &gt; Boot-Repair-Disk &gt; &quot;found EFi&quot;, check settings"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by juka2 on 2014-08-23
Hi,

i'm new to ubuntu, used 12.04 without any problems, now I upgraded from 12.04 to 14.04, afterwords my computer doesn't boot any more. 
So I started the "Boot-Repair-Disk", it tells me "Found EFI, check settings" and stops repairing... than it offers to install 13.04(?) for repair, but in advance i should save my data.. (where??)

I've got an "Boot-Info Skript", but can't get an internet connection... 

I'm very glad for any kind help!

---

### Post by fantab on 2014-08-23
Boot-info script provides valuable info about your machine's 'boot' process.
We'd need to look at it.

If re-installing Ubuntu is an option and if you have all your important data backed up then reinstall Ubuntu.

---

### Post by juka2 on 2014-08-23
Hi,

booting computer leads to:
 error: file not found
grub rescue> _

Reinstalling Ubuntu is no option, as upgrade-option i've choosen "upgrade to 14.04 and keep data", unfortunately i didn't save in advance.. 

Boot-Repair-Disk displays the follwing messages:
1. EFI entdeckt, überprüfe Einstellungen >> found EFI, check settings
2. Achtung, dies wird notwendige Pakete von Ubuntu 13.04 Repository installieren. bitte sichern Sie ihre Daten vor diesem Vorgang. >> necessary software package of ubuntu 13.04 repository will be installed. in advance save your data

As i don't have internet access i only can type the textfile: hope these informations help:

Boot Info Summery
=> grub2 (v.199) is installed in the MBR of /dev/sda and look at sector ... of the same hard drive for core.img. core.img is at this location and looks in partition 112 for .

sda1: 
Filesystem: vfat
boot sector type: - 
boot sector info: no errors found in the boot parameter block.
operation system: 
boot files: /EFI/ubuntu/grubx64.efi

sda 2:
Filesystem: ext4
boot sector type: - 
boot sector info: 
operation system: ubuntu 14.04.1 LTS 
boot files: /boot/grub/grub.cfg /etc/fstab
               /boot/grub/i386-pc/core.img

sda3:
file system: swap
boot sector type: - 
boot sector info:

Then the drive/partition Infos follow, but i guess you're look just for boot info summery?

hopefully this helps, thanks for any further help!!

---

### Post by ajgreeny on 2014-08-23
How did you do the upgrade? Was it a re-install of the new version over the old, and if so I hope you used the "Something Else" option at partitioning stage or you may have inadvertently overwritten and removed all your files.

This may not be a very helpful comment at this stage, but it is very unwise ever to carry out any partition editing or distro upgrading without first ensuring you have full and restorable backups oryoumay fall foul of the bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by juka2 on 2014-08-23
i downloaded the software update iso-image from here [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) ... in the menu i choosed the option called something like "upgrade from 12.04 to 14.04 directly and keep your data"...

---

### Post by fantab on 2014-08-24
I think you are safe with your data... lets check.
Boot with the Ubuntu DVD/USB and "Try Ubuntu"... look for your data in the file browser.
While you are at it and if your data is still there, it will be good time to back up your important data.

Try [Boot-Repair tool]("https://help.ubuntu.com/community/Boot-Repair") after you have backed up your data.  edit: by the way, you must get online to download and install Boot-repair tool.
Create bootinfo summary and note the url to the file.
Run recommended repair.
Create bootinfo summary and note down the url to the file.

Reboot.

If boot problems continue then post the bootinfo urls here.

---

