---
title: "grub lost, re-install grub does not work"
date: 2018-12-29
forum: Installation &amp; Upgrades
---

### Post by kornelixgmx.de on 2018-12-29
[SIZE=3][FONT=courier new]I have a multi-boot configuration with 5 Linux flavors (for software testing). 
I got the bright idea of removing the grub package from all but Ubuntu 18.10
(because in the past some updates destroyed my multi-boot menu)
Now I cannot boot and cannot re-install a working grub. 

What I did up to now: 
Boot the 'super grub disk' CD. 
From this CD menu, boot to Ubuntu 18.10. 
Install grub in the normal manner. 
Computer does not boot. I get a blank screen.

Here are the outputs when I installed grub:

mico $: sudo update-grub
[sudo] password for mico: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.18.0-13-generic
Found initrd image: /boot/initrd.img-4.18.0-13-generic
Found Ubuntu 18.04.1 LTS (18.04) on /dev/nvme0n1p4
Found Ubuntu 16.04.5 LTS (16.04) on /dev/nvme0n1p5
Found Fedora 29 (Workstation Edition) on /dev/nvme0n1p6
Found Ubuntu Disco Dingo (development branch) (19.04) on /dev/nvme0n1p7
Adding boot menu entry for EFI firmware configuration
done

mico $: sudo grub-install
Installing for x86_64-efi platform.
Installation finished. No error reported.

-----------------------------------

At this point the following conditions were noted:

/dev/nvme0n1p1 is mounted at /boot/efi
/boot/efi shows these files with a current time stamp:
   /boot/efi/BOOT/BOOTX64.EFI
   /boot/efi/ubuntu/grub64.efi

Also tested:   
sudo grub-install /dev/nvme0n1  (device only)
sudo grub-install /dev/nvme0n1p1  (boot partition)
sudo grub-install /dev/nvme0n1p3  (Ubuntu 18.10 partition)
The results are the same: boot produces a blank screen
[/FONT][/SIZE]
At this point the only cure I know is to re-install Ubuntu.
(or hope for a response to this message)

---

### Post by yancek on 2018-12-29
You need to tell Grub where to install which you left off in the command you posted.  If you have the efi partition mounted at /boot/efi, the command below should work.  YOu should also have more directories in the boot efi directory, at least another fedora directory.  Not sure what to expect with multiple Ubuntu installs in EFI.  If that doesn't work, you might have to run boot repair with the Create BootInfo Script option and post that link here which will give more details.

> [SIZE=3][FONT=courier new]sudo grub-install /dev/sda[/FONT][/SIZE]

---

### Post by oldfred on 2018-12-29
Have they updated Supergrub to work with UEFI? I thought you have to use Rescatux.
 [https://www.supergrubdisk.org/rescatux/](https://www.supergrubdisk.org/rescatux/)


There also is rEFInd for UEFI systems, but it can reboot to boot a BIOS install.
 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) 


 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by kornelixgmx.de on 2018-12-29
The magic recipe is:
   sudo update-grub
   sudo grub-install --force /dev/nvme0n1 

--force is an undocumented necessity for nvme disk
(error messages are produced and can apparently be ignored)

boot partition can be omitted (as above) or included, e.g. nvme0n1p1

---

