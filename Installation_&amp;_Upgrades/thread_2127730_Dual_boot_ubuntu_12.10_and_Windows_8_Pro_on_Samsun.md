---
title: "Dual boot ubuntu 12.10 and Windows 8 Pro on Samsung Series 9 NP900X4C-A02"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by Kathees on 2013-03-20
Hi All,

I managed to install ubuntu by allocating separate partition on my laptop. In order to do that I had to disable "secure boot" and select "CMOS" as boot type. Then it's successfully boot my USB and installed.

Now my issue is whenever I start my PC it's directly going to Ubuntu. If I change the boot type to "UEFI" or "UEFI and CMOS" it's directly going inside Windows. SO it's came down to BIOS change every time I want to boot into different OS.

I searched something and find these links useful.

[http://askubuntu.com/questions/233275/how-to-dual-boot-ubuntu-windows-8-on-a-samsung-series-9-laptop](http://askubuntu.com/questions/233275/how-to-dual-boot-ubuntu-windows-8-on-a-samsung-series-9-laptop)

As the thread owner suggested I followed official method.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) (Part 5 in the Installing Ubuntu Quickly and Easily via Trial and Error section).


But when I try to use Boot repair I'm having issues. After running this first it ask me to enter the following commands in terminal.

```
[COLOR=#000000][FONT=arial]sudo chroot "/mnt/boot-sav/sda9" dpkg --configure -a[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]sudo chroot "/mnt/boot-sav/sda9" apt-get install -fy[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]sudo chroot "/mnt/boot-sav/sda9" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*[/FONT][/COLOR]
```

At the end of these commands it said like going to remove GRUB. Once I did I can't boot Ubuntu etc. I select "YES" for that.

Again Boot repair asked me to enter the following command. I think this is to install GRUB again.

```
[COLOR=#000000][FONT=arial]sudo chroot "/mnt/boot-sav/sda9" apt-get install -y --force-yes grub-efi linux[/FONT][/COLOR]
```

When I enter this in the Boot repair windows there is a progression bar saying "GRUB is installing. This might take several minutes". But my machine stuck at this step for hours.

After like 1 hour I cancelled and ran Boot repair again. This time it's directly goes to the stuck step (Installing GRUB) and takes forever and install nothing.

I cancelled and rebooted machine and now machine is asking for grub recovery.

By changing boot type I can still login to Windows 8. Please help me what should I do to fix this. I really need both Windows and Ubuntu!

---

### Post by oldfred on 2013-03-21
I do not know the exact commands Boot-Repair is having you do to chroot into your install. It is trying to uninstall grub-pc (BIOS) and reinstall grub-efi (UEFI).

But to get grub to correctly install in chroot you have to mount not just the main install but the efi partition, so it knows where grub has to install its efi files. Did you mount the efi partition?

It should be like this? But use your main install (sda9) and efi partition (? example uses sda1). 

 efi chroot:
sudo mount /dev/sda9 /mnt #sda9 is my root partition
sudo mount /dev/sda1 /mnt/boot/efi #sda1 is my efi partition
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo cp /etc/resolv.conf /mnt/etc/ #makes the network available after chrooting
sudo chroot /mnt
apt-get install --reinstall grub-efi-amd64

   or alternatively: 
apt-get install --reinstall grub-efi
update-grub

---

### Post by Kathees on 2013-03-21
> **oldfred said:**
> I do not know the exact commands Boot-Repair is having you do to chroot into your install. It is trying to uninstall grub-pc (BIOS) and reinstall grub-efi (UEFI).

But to get grub to correctly install in chroot you have to mount not just the main install but the efi partition, so it knows where grub has to install its efi files. Did you mount the efi partition?

It should be like this? But use your main install (sda9) and efi partition (? example uses sda1). 

 efi chroot:
sudo mount /dev/sda9 /mnt #sda9 is my root partition
sudo mount /dev/sda1 /mnt/boot/efi #sda1 is my efi partition
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo cp /etc/resolv.conf /mnt/etc/ #makes the network available after chrooting
sudo chroot /mnt
apt-get install --reinstall grub-efi-amd64

   or alternatively: 
apt-get install --reinstall grub-efi
update-grub

Thank you very much for your reply. I think I have made some mistakes while install. Like I said I haven't install as EFI. I changed the boot type to CMOS.

I only created 2 partition 1 for "/" and another one for "swap". Then ubuntu asked me I should create a "/boot" partition. (Also it's said it's not normal /boot mount). SO I created a small partition with 10MB (It's says 4MB enough). I'm not sure which partition you mean by "efi" partition? Is that 3rd one? If not how can I create one? I can reinstall Ubuntu again as long as it doesn't affect my Windows.

---

### Post by oldfred on 2013-03-21
I do not think it was asking for the /boot partition but a bios_grub partition?

bios_grub is unformatted space for grub to install part of its boot code into. It just needs to be a 1MB unformatted partition anywhere on the drive. The bios_grub is required with gpt partitioning and BIOS/CSM/Legacy mode booting.

A /boot partition is not usually required for Desktops, but often for servers. It often is 250 to 400MB and formatted ext2 but each user has their own needs.

A efi partition is required if booting with UEFI. But you can only have one efi partition per drive, so Ubuntu would share the efi partition that Windows already has. Every operating system in the efi partition creates folders with its name.

Post the link from a run of the BootInfo report from Boot-Repair.

---

### Post by Kathees on 2013-03-22
> **oldfred said:**
> I do not think it was asking for the /boot partition but a bios_grub partition?

bios_grub is unformatted space for grub to install part of its boot code into. It just needs to be a 1MB unformatted partition anywhere on the drive. The bios_grub is required with gpt partitioning and BIOS/CSM/Legacy mode booting.

A /boot partition is not usually required for Desktops, but often for servers. It often is 250 to 400MB and formatted ext2 but each user has their own needs.

A efi partition is required if booting with UEFI. But you can only have one efi partition per drive, so Ubuntu would share the efi partition that Windows already has. Every operating system in the efi partition creates folders with its name.

Post the link from a run of the BootInfo report from Boot-Repair.

Hi, thanks for the reply and sorry for late response. You might be correct about saying bios_grub partition. I didn't remember what it asked me at the start. 

So if I want to install in efi mode is it different procedures than the previous one? How should I set the partitions? I hope it will not overwrite my Windows. Or can I still modify without reinstalling?

Sorry boot-repair not finishing the operation so I couldn't get the URL... Let me know if you need any additional info. Thanks in advance for helping :)

---

### Post by oldfred on 2013-03-22
If you want to install in UEFI mode you have to boot installer in UEFI mode. Then it automatically installs in UEFI mode. Grub2's efi files will be installed to a ubuntu folder in the existing efi partition.

Best to backup efi partition and all of Windows first.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

