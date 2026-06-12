---
title: "Upgrading to 14.04 with Grub 0.9"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by kkkkdddd on 2014-08-03
I have 6 years old laptop (Dell XPS M1530).

It had Ubuntu 8.04. Then I updated to 10.04, and then to 12.04.
Now I want to update to 14.04.

The computer still has Grub Legacy because distribution upgrades haven't installed new one.

Are there any known issues with such an upgrade?

---

### Post by oldfred on 2014-08-03
I think I converted my current, but 2006 (and updated some ) system with 10.10 to grub2. 
Then they had a grub2 test install that you booted from grub legacy and only after it worked did you uninstall grub legacy.

You can back up your menu.lst and if necessary reinstall grub legacy from a live installer. Back with 10.10 I did not like grub2 as it was a lot different and it was not well documented. 
But now I install grub2 to every bootable drive or flash drive. 

Boot-Repair also has a full uninstall of grub & reinstall in Advanced options which I think will also uninstall grub legacy.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Just make sure you have a working live installer in case you need to make repairs and that Internet is working as it has to download the new grub2 packages. While grub legacy is uninstalled but before grub2 is reinstalled you will not be able to reboot, so do not interrupt that reinstall process. 


 # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub


From a live installer you can chroot to install grub or  grub2, but need to purge old version first.

 It is essentially the same as above commands, but you have to chroot first.

package grub is grub legacy, package grub-pc is the BIOS boot version of grub2. grub-common is used by both, but needs to also be purged & reinstalled ( I think). 


 # kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)
# HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

