---
title: "Problems removing grub-customizer"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by cackerso on 2014-01-10
I installed grub-customizer and it worked ok for a while.  Then I  started getting problems, mainly with the menu listings.  As a backup I  installed another linux dist on my second hard drive so I could boot  from there if there were any problems.  Then I proceeded to uninstall  grub-customizer according to the FAQ listed here:

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)    

The suggested removal proceedure is item #7 at the end.  When I got done and I ran update-grub, I got the following error:

/etc/grub.d/10_linux_proxy: 3: /etc/grub.d/10_linux_proxy: /etc/grub.d/proxifiedScripts/linux: not found
/etc/grub.d/10_linux_proxy: 3: /etc/grub.d/10_linux_proxy: /etc/grub.d/bin/grubcfg_proxy: not found

So I don't want to install this version to the MBR until I have cleared up the problem.  I'm running Kubuntu 12.04

During an software upgrade I also got the following error which seems related"

"The following errors occurred while applying changes:

Package: grub-pc
Error: subprocess installed post-installation script returned error exit status 127"

---

### Post by oldfred on 2014-01-10
Any proxy file in grub is from Grub customizer.

It may be easier to move the entire /boot/grub folder and do a clean install of grub.

If you can boot.

 # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

You may be able to use Boot-Repair and its chroot or use Supergrub to boot.

---

### Post by cackerso on 2014-01-13
Well, the first pass using your suggestion didn't work.  However what did seem to work OK was going to the /etc/grub.d directory and moving everything with "proxy" in it's name to a separate (new) folder.  Then I ran the commands you posted and it all seems to be fine now.  Thanks.

---

