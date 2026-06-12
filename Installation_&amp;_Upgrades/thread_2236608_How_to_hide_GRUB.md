---
title: "How to hide GRUB"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by John_Squar on 2014-07-27
I installed Ubuntu 14.04 LTS to a fresh drive, and things worked without problems.

Then I cloned the drive to another fresh drive in the same computer with Clonezilla, and it worked, but for some reason I now have to deal with the GRUB boot menu on both drives when I boot to them.  I want to disable this, so that the Ubuntu on the primary drive is always directly booted to unconditionally, without any sort of menus or choices.

I've tried messing around with the GRUB settings, using these commands:
sudo gedit /etc/default/grub
then I save the changes and use
sudo update-grub

I've messed around with some of these settings and followed a few suggestions from other forum posts and such, but nothing I do seems to change anything.  Here's how my grub file looks now:

GRUB_DEFAULT=0

GRUB_HIDDEN_TIMEOUT=0

GRUB_HIDDEN_TIMEOUT_QUIET=true

GRUB_TIMEOUT=0

GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

GRUB_CMDLINE_LINUX=""


I still get the GRUB menu when I boot up.  How can I change this?

If it matters, the computer has 4-5 other hard drives with Ubuntu on them, but I only care about booting from the primary hard drive.

---

### Post by oldfred on 2014-07-27
You can always turn off os-prober. 
I know if grub only find one install it directly boots. Not sure if os-prober off will do that or not?

       sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

If you cloned drive, did you change UUIDs?
Post this to be sure.
      
 sudo blkid -c /dev/null -o list

I do not like changing timeout to 0. It then can be difficult to bring up grub menu if needed. Often better to set to 1 or 2 seconds, so you have a chance to get to menu.
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

