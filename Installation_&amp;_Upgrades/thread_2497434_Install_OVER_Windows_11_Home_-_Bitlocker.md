---
title: "Install OVER Windows 11 Home - Bitlocker"
date: 2024-05-04
forum: Installation &amp; Upgrades
---

### Post by jdavidroberts on 2024-05-04
I am trying to blow away an installation of Windows 11 Home on my daughter's old laptop and replace it with Ubuntu Desktop.  The Ubuntu installer says that Bitlocker is installed and forces me to reboot into Windows to turn off Bitlocker.

In Windows, amazingly, there is no way to turn off Bitlocker.  I am logged in as administrator and yet no way to turn it off.  I also can't find an option to uninstall Windows.  And yes, the Windows UI says that I am logged in as an Administrator.

I've searched a ton online and gone in a lot of circles.  The Ubuntu documentation I found suggests it IS an option to just reformat the whole drive and throw away all the encrypted data.  I would love to do this.  But the Ubuntu install doesn't seem to offer it.  When I choose to overwrite, with or without LVM, it takes me to a page where the only option is to reboot to Windows and turn off Bitlocker.  If I go into the advanced options, there doesn't seem to be a way to select the main partition to install Ubuntu on.

What am I missing?  Thanks.

---

### Post by oldfred on 2024-05-04
One possible solution:
[https://askubuntu.com/questions/1305270/bitlocker-is-blocking-ubuntu-20-04-installation-in-a-dual-boot-system-with-windo](https://askubuntu.com/questions/1305270/bitlocker-is-blocking-ubuntu-20-04-installation-in-a-dual-boot-system-with-windo)

---

### Post by tea for one on 2024-05-05
> **jdavidroberts said:**
> The Ubuntu documentation I found suggests it IS an option to just reformat the whole drive and throw away all the encrypted data.  I would love to do this.  But the Ubuntu install doesn't seem to offer it. 
Boot into a "Try Ubuntu" session
Do not start the installation  process
Open Gparted
Unmount partitions (if mounted)
Create a GPT (GUID partition table) on your target disk

This will remove all the existing partitions
Edit: I would take an image of your Windows system first, because - you never know?

---

### Post by jdavidroberts on 2024-05-05
Thank you It says it is not mounted.  The Mount option is disabled.  I see "Format to", should I try that?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293729&stc=1[/IMG]

---

### Post by jdavidroberts on 2024-05-05
Those options aren't available for me in Windows, even though I am logged in as an Administrator.

---

### Post by karyk on 2024-05-05
> **jdavidroberts said:**
> 
What am I missing?  Thanks.

I don't have a non-Pro version of Windows 11, but in Windows 11 Home Microsoft added device encryption that is similar to and based on Bitlocker, but not Bitlocker.  Try under Privacy and Security to turn off device encryption.  I believe it is turned on by default.

---

### Post by oldfred on 2024-05-05
At the top of gparted is Device.
A blank drive defaults to MBR, but you can change to gpt which for UEFI you want.
Since drive is gpt, not sure but I expect changing it to gpt may erase drive.

MBR & gpt are not compatible, so the change totally erases a drive.

Also NVMe has some higher level commands
sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
nvme --help
sudo nvme list

[FONT=monospace][COLOR=#000000]sudo nvme id-ctrl /dev/nvme0 -H | grep -E 'Format |Crypto Erase|Sanitize'[/COLOR]
If sanitize supported. totally erases drive. Will be quick as it internal resets NVMe encryption.
sudo  [/FONT]nvme-sanitize
[FONT=monospace]
[/FONT]

---

### Post by jdavidroberts on 2024-05-07
Switching to gpt worked as a way to reformat.  Thanks!

---

### Post by karyk on 2024-05-08
Just curious whether you tried my method of turning off device encryption in Windows?

---

### Post by MAFoElffen on 2024-05-09
> **jdavidroberts said:**
> I am trying to blow away an installation of Windows 11 Home on my daughter's old laptop and replace it with Ubuntu Desktop.  The Ubuntu installer says that Bitlocker is installed and forces me to reboot into Windows to turn off Bitlocker.

In Windows, amazingly, there is no way to turn off Bitlocker.  I am logged in as administrator and yet no way to turn it off.  I also can't find an option to uninstall Windows.  And yes, the Windows UI says that I am logged in as an Administrator.

I've searched a ton onlinrives that had pre-existing Volume managers, such ase and gone in a lot of circles.  The Ubuntu documentation I found suggests it IS an option to just reformat the whole drive and throw away all the encrypted data.  I would love to do this.  But the Ubuntu install doesn't seem to offer it.  When I choose to overwrite, with or without LVM, it takes me to a page where the only option is to reboot to Windows and turn off Bitlocker.  If I go into the advanced options, there doesn't seem to be a way to select the main partition to install Ubuntu on.

What am I missing?  Thanks.
In Windows, if you open the 'Control Panel' > Search for Bit Locker . Under that section there are options to "suspend bitlocker". "Suspend BitLocker" turns it off. This is what I suggest to people if they are going to install alongside of Windows with it having bitlocker.

Another way is to zero the drive. This is what I do for encrypted drives such as Bitlocker or LUKS), Volume Managers such as LVM2 or ZFS, or had software RAID such as mdadm. The way I do that is to boot from an Ubuntu LiveUSB > Use "Try". > Open a terminal session, then do: The example give is if /dev/ada is the disk I want to zero...)
```

sudo su -
blkdiscard -f /dev/sda
wipefs -a /dev/sda
sgdisk --zap-all /dev/sda

```
Everything will be gone, inside and outside the, and including the partitions & partition tables. It will be clean, and ready for any kind of install.

Then just start up the installer and you can do whatever you want on that clean disk.

---

