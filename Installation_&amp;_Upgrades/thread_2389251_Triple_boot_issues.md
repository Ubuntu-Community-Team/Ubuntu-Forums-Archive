---
title: "Triple boot issues"
date: 2018-04-13
forum: Installation &amp; Upgrades
---

### Post by cackerso on 2018-04-13
I got a new hard drive. I set up the system as UEFI only and partitioned  the drive accordingly. I created a partition for Windows 10 and  installed it.I set up partitions for Kubuntu 16.04 and Ubuntu 17.04. I  installed them. Everything went fine. I had no problems booting, GRUB  came up with all three OS's and I could boot into all three. At some  point Kubuntu and Ubuntu upgraded their respective kernels. The updater  ran "update-grub". I had no problems and things continued to boot just fine.

It's clear from from the boot order in the GRUB boot screen that the  grub configuration file for boot came from the Ubuntu installation, the one I  installed last.  My question is can I use some version of "grub-install" to switch the  boot loader to use the Kubuntu installation configuration file? I assume the installers ran  some version of this when the installed the OS. My /boot/efi partition  is sda2. So will running "grub-install /dev/sda"  from Kubuntu do what  I'm looking to do or do I run "grub-install /dev/sda2", or something else ? Someone suggested I run" sudo grub-install from the Kubuntu install. I did and it made the Ubuntu install unbootable.  When I re-installed it everything worked OK again. I know I can just edit the etc/default/grub file to change which OS boots first but it would be useful at some point to be able change which configuration file the boot file uses.

Just a note, when I boot Kubuntu now  a couple of lines  appear during the boot. 

Couldn't get size: 0x800000000000000e
MODSIGN: Couldn't get UEFI db list
Couldn't get size: 0x800000000000000e

 Then it  boots fine. What do the lines mean? Is there something I should fix?

---

### Post by oldfred on 2018-04-13
I think I get similar errors, have just ignored them.

With UEFI you install to a drive like sda, just like you do with BIOS installs. Its just that in UEFI boot mode it always installs grub into ESP - efi system partition on first drive.

I have not tried installing grub from any of my additional installs. I just edit /boot/efi/EFI/ubuntu/grub.cfg
and to see UUIDs.
       sudo blkid -c /dev/null -o list 
    or
       lsblk -f 
    
sudo nano /boot/efi/EFI/ubuntu/grub.cfg
```
#search.fs_uuid 69333549-6680-4072-bdcb-94e333ab044c root hd2,gpt3 
search.fs_uuid 5c1e1a3f-261f-4da5-a0c2-8f479b3039de root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by ajgreeny on 2018-04-13
I have similar errors to those you show at the end of your post showing in all my 18.04 installations, both to hard metal and as VMs in VirtualBox, but all the OSs boot fine and run well, so like oldfred I have also ignored them.

I do not see the errors in any of my installations of 16.04, whether hard metal or VMs, only in 18.04.

My hard metal installs are all UEFI but the VMs, of course, are using BIOS from VBox.

---

### Post by nlee2 on 2018-04-13
Have you tried changing the boot order in the UEFI firmware or using efibootmgr -o?

---

### Post by Dennis N on 2018-04-13
> My question is can I use some version of "grub-install" to switch the boot loader to use the Kubuntu installation configuration file?

The original Kubuntu files are gone (overwritten by Ubuntu) but, the files in the EFI system partition used by Kubuntu and Ubuntu are the same, except for the UUID and root location given in the file /EFI/ubuntu/grub.cfg. So you just modify the grub.cfg made by Ubuntu to load Kubuntu instead of Ubuntu. User oldfred shows the file to edit to do this. Very easy.

---

### Post by cackerso on 2018-04-14
Thanks for the solutions.

---

