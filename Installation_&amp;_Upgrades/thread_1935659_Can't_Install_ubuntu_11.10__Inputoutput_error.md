---
title: "Can't Install ubuntu 11.10 : Input/output error"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by galmeida on 2012-03-04
**[SIZE="3"]SOLVED: it was a problem in the ram memory module. I recommend the ultibateboot cd for tests[/SIZE]**


This is a known problem but i couldn't fix with what I've found on web.

**Task and error:**
[LIST]
[*]Install ubuntu 11.10 on an empty HDD.
[*]I get a Errno5(input/output error) always on the same stage (around 30%). The systemn suggestion is about burning the CD in low speed(but in this case is a flash drive) and checking the HDD for errors. 
[*]A single time, instead of the error above, I got a 'the following file didn't match its source copy on the cd/dvd - target/usr/lib/cups/filler/hpcups" then another one ofr another file, the finally errno5
[/LIST]

**Method:**
  startable flash drive created with usb-creator-gtk

**Inventory:**
[LIST]
[*]asus p8h61-mx
[*]   i3 2100
[*]   A single 4gb memory module
[*]   ubuntu 11.10 desktop amd64
[*]   500 GB HDD with no OS installed.
[/LIST]


**Tests made:**
[LIST]
[*]HDD self-test: No errors
[*]  check disk option from flash boot: No errors
[*]  startable flash drive checksum: No erros
[*]  Try with another physical flash drive: No effect
[*]  Using ubiquity --no-migration-assistant ([http://ubuntuforums.org/showthread.php?t=1910258](http://ubuntuforums.org/showthread.php?t=1910258)) method: No effect
[/LIST]

**Tests not made:**
[LIST]
[*]memtest86 - No tools yet.
[*]   fsck -cc - It would last about 10h and I don't know if it has advantages over HDD self test.
[*]   Removing a Ram module - I got only one.
[*]   Burning the CD slower - checksum was fine and I was able to install with the same flash drive eralier(see history)
[/LIST]

**History:**
   The desktop is **_new_** and it had windows 7 ultimate installed. I was able to install ubuntu 11.10 along with it correctly, but the bootloader selection was leavning me on a grub prompt, like 'grub>', and I had to run commants like "root (hda,b)  kernel /vmlinus ... boot" to boot everytime.
   I tried many things and couldn't fix it, but at least it was still working. Then I followed this guys instructions [http://askubuntu.com/questions/108375/skip-grub-prompt-in-dual-boot-win7-ubuntu-11-10](http://askubuntu.com/questions/108375/skip-grub-prompt-in-dual-boot-win7-ubuntu-11-10) and my system stopped booting at all.
    So I decided to format and reinstall everything, but this time starting with ubuntu.

**Wishes**
[LIST]
[*]To know if fsck -cc can find errors that hdd self test can't
[*] To know how likely it is to be a hardware defect
[*] More tests and actions to try and post the result
[*] An indication of another user friendly distro where this bug doesn't occur
[/LIST]

**Thanks in advance**

---

### Post by oldfred on 2012-03-04
How large was hard drive? There are some bugs where / (root) partitions over 500GB cause issues. Have you tried formating in advance with gparted and then using manual install (something else) to choose partitions. 

I normally suggest a smaller / of 10 to 25GB, swap of 2GB or the size of RAM in GiB ( about 4.4GB in your case) if you want to hibernate and the rest as /home. If dual booting with Windows you may want /home not as large and save most data into a shared NTFS data partition. Best not to write directly into Windows system (c:) partition from Ubuntu.

If you need to make repairs of grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

And a good tool to make minor repairs or run the boot info script so we can suggest major fixes.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

More advanced, if drive is only going to be Linux, you might want to consider gpt instead of MBR(msdos). GUID(gpt) is the new partitioning system but does not work with Windows unless you boot with UEFI not BIOS. You have to have another small 1MB bios_grub partition for gpt to work.

---

### Post by galmeida on 2012-03-04
> **oldfred said:**
> How large was hard drive? There are some bugs where / (root) partitions over 500GB cause issues. Have you tried formating in advance with gparted and then using manual install (something else) to choose partitions. 

I normally suggest a smaller / of 10 to 25GB, swap of 2GB or the size of RAM in GiB ( about 4.4GB in your case) if you want to hibernate and the rest as /home. If dual booting with Windows you may want /home not as large and save most data into a shared NTFS data partition. Best not to write directly into Windows system (c:) partition from Ubuntu.

If you need to make repairs of grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

And a good tool to make minor repairs or run the boot info script so we can suggest major fixes.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

More advanced, if drive is only going to be Linux, you might want to consider gpt instead of MBR(msdos). GUID(gpt) is the new partitioning system but does not work with Windows unless you boot with UEFI not BIOS. You have to have another small 1MB bios_grub partition for gpt to work.

The whole HDD is 500gb.

I don't have any OS installed and my problem is not being able to install ubuntu. So I don't understand how a boot repair could help me.

---

### Post by oldfred on 2012-03-04
When you had the grub> prompt the tools to fix it may have helped. 

Not sure about the specific error on install  you now are getting. You have already gone thru many of the verification steps to make sure ISO and install medium is good.

With an i3 you have a system that may use UEFI is that part of the issue. Not sure how Ubuntu checks to know if system is in UEFI or BIOS mode. Most have found with UEFI partitioning in advance works best as then the efi partition is created. Even with BIOS I find partitioning in advance helps simplify install.

---

### Post by galmeida on 2012-03-24
It was a  problem in the RAM module.

---

