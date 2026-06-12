---
title: "Dual Ubuntu Root Partitions"
date: 2016-05-31
forum: Installation &amp; Upgrades
---

### Post by Etienne_Martel on 2016-05-31
Hello,

I would like to install a x86_64 server with two independent Ubuntu root partitions side by side. This is a concept similar to networking equipment in which you can have co-resident firmware versions and choose which one to boot from when upgrading the system.

This way I could clone partitions (partimage), transfer them and restore them. While at the same time allowing to boot into each, one at a time.

The systems run UEFI.

My target partition schema is as follows:

[TABLE="width: 500"]
[TR]
[TD]Size[/TD]
[TD]Type[/TD]
[TD]Mount point[/TD]
[TD]Comment[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]50MB[/TD]
[TD]EFI[/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]500MB[/TD]
[TD]ext4[/TD]
[TD]/boot[/TD]
[TD]shared boot partition[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]20GB[/TD]
[TD]ext4[/TD]
[TD]/[/TD]
[TD]first root partition[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]20GB[/TD]
[TD]ext4[/TD]
[TD]/[/TD]
[TD]second root partition[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]16GB[/TD]
[TD]swap[/TD]
[TD][/TD]
[TD]shared swap[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]rest[/TD]
[TD]ext4[/TD]
[TD]/var/lib/libvirt/images[/TD]
[TD]shared Qemu/KVM images folder[/TD]
[TD][/TD]
[/TR]
[/TABLE]

I tried achieving this install numerous times with different options and a different process with both Ubuntu 14.04 and 16.04 without success.

I figured I would install once all the way through using the first 20GB partition as /, complete the install, then go through it again using the 2nd 20GB as / while remapping all the rest of the partitions (without formatting of course) in the partition manager.

It always ends the same, the system works perfectly after the 1st install but will not boot to a prompt after the 2nd install complaining it cannot find a partition. 

Most dual boot resources are covering Windows (or sometimes Mac OS X) and Ubuntu coexistence.

Can you point me to a good reference for dual Ubuntu OS? 

Please keep in mind that the install will start off with two root partitions containing the same Ubuntu version.

I also need Grub to automatically and gracefully detect both root partitions and update its configuration accordingly when updates are applied.

---

### Post by oldfred on 2016-05-31
You cannot nor should not share /boot.
It leads to conflicts.

Each install has its own configuration. Grub, fstab and other settings are unique to each install.
I do have multiple installs and boot each separately in UEFI, but /EFI/ubuntu/grub.cfg is overwritten with each install and its UUIDs. So from UEFI I cannot directly boot each install, but do boot from grub menu.

I also share data partition and back that up separately. And on main working install backup /home, so I could restore it easily if needed. But generally my other installs are tests of something or a newer version to see what has changed.

---

### Post by Etienne_Martel on 2016-05-31
Thank you for the prompt response.

I also encountered the problem of the unique /EFI/ubuntu/grub.cfg preventing dual boot directly from the UEFI menu. Hence my idea of a single /boot to point to each root partitions. 

Otherwise my issue becomes that I have the complexity of maintaining two grub installs and configuration files that are almost the same but not quite the same while not benefiting from the redundancy because UEFI won't let me point to both. 

Is there any way to achieve what I am looking for more elegantly?

fstabs would remain separate.

---

### Post by oldfred on 2016-05-31
I have configured a grub.cfg in the ESP to boot ISO directly. I just manually edited it. But it was a grub install to a flash drive directly, so it has some supporting files.

I would think with a full install, you can edit the grub in the ESP. It may need the rest of grub like a full install of grub to an external drive, so it has its scripts and other files. 

       sudo grub-install --target=x86_64-efi --root-directory=/media/flashdrive --removable --modules=part_gpt
sudo grub-install --target x86_64-efi --efi-directory /mnt --boot-directory=/mnt/boot --removable
Also need fonts & modules
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
grub-mkimage -O x86_64-efi -p /grub -c mnt/grub/embed_efi.cfg -o mnt/EFI/BOOT/bootx64.efi configfile fat part_gpt part_msdos cat echo test search search_label search_fs_uuid boot chain linux reboot halt normal efi_gop efi_uga font gfxterm
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

This site has lots of useful info. You can have UEFI directly boot kernel or use his rEFInd which also is fully in the ESP to boot.

 Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

### Post by ubfan1 on 2016-05-31
Well, there are many solutions, you can judge how elegant they are.
As you have noted, the bottleneck is the wired in /EFI/ubuntu/grub.cfg which the grub.efi uses.

1) Brute force, just use a different bootloader than grub on one device (or one which allows you to select different configuration files).  I cannot 
advise on which, I use grub.
2) Pretty brutish, add a second boot device, with its own EFI partition with a different /EFI/ubuntu/grub.cfg file.  Even a USB stick could be used for this.
The EFI could then easily select which to run.
3) The /EFI/ubuntu/grub.cfg file is pretty static -- it's a three liner with a UUID of a root wired in -- that doesn't change often for any one system.  There is no
need to use a UUID even, just specify the disk/parameter directly.  So, you can just add another configfile line and bring in the other root's grub.cfg file.  You'd want to 
pretty things up by editing the /etc/grub.d files on each system, but after that, no maintenance would be needed (unless you changed a root partition).

---

