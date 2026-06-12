---
title: "Dual booting Ubuntu Studio 14.04 with Windows 8.1 in UEFI mode"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by Rijul_Ahuja on 2014-04-27
Hello everybody.

I bought a new laptop which came with Windows 8 pre-installed, and it uses UEFI.
I downloaded the Ubuntu Studio 14.04 ISO, created a bootable pendrive using Rufus using the GPT partition scheme for UEFI computer.
I then booted into the LiveCD, and choose to try Ubuntu Studio without installing. Inside the OS, I ran the Ubiquity installer, which ran, but threw an error "**grub-efi-amd64-signed failed to install into /target/**" , and crashed.
Then, I ran boot repair using recommended repair, it did some things, but it gave an error "**Please close all your package managers (Software Center, Update Manager, Synaptic, ...) Then try again"**. I did generate the boot repair information manually, present [here]("http://paste.ubuntu.com/7344766/").
Now, when I turn on my system, I do not see GRUB, it boots directly into Windows. 
Please help. It's really appreciated.

Regards,
Rijul Ahuja

---

### Post by oldfred on 2014-04-28
I think the errors you are getting is that you have a separate /var. Boot-Repair has the option to also mount a separate /boot but not the /var.
You probably have to manually reinstall grub to drive as you show no ubuntu folder in the efi partition. And you have to be sure to mount all separate partitions.

Most desktops do not need separate /boot nor /var partitions. Either /home or data partitions then work with a smaller 20 or 25GB / (root) partition.

I do not know with separate /var if Supergrub will let you boot, so then you can more easily reinstall grub from inside your install.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

You will also have to mount /boot & /var

 UEFI chroot:
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

### Post by Rijul_Ahuja on 2014-05-04
Thank you for your help. I set up the installation without a seperate /var, and it worked.
Regards,
Rijul Ahuja

---

