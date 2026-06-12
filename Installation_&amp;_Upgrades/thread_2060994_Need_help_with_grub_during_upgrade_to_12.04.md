---
title: "Need help with grub during upgrade to 12.04"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by freakdaddy on 2012-09-21
Got this message doing upgrade from 11.10 server to 12.04 server.  No idea what to do...  any tips?
--------------------------------------------------------------------------------------------

The  GRUB boot loader was previously installed to a disk that is no longer  present, or whose unique identifier has changed for some reason. It is  important to make sure that the installed GRUB core image stays in sync  with modules and grub.cfg. Please check again to make sure that GRUB is  written to the appropriate boot devices.

If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.

Note:  it is possible to install GRUB to partition boot records as well, and  some appropriate partitions are offered here. However, this forces GRUB  to use the blocklist mechanism, which makes it less reliable, and  therefore is not recommended.

GRUB install devices:                                                                                                           
[ ] /dev/sda (4000730 MB; ???)
[ ] - /dev/sda2 (255 MB; /boot)
[ ] /dev/sdb (2000365 MB; ???)
[ ] /dev/dm-0 (3949671 MB; rmt170-root)

---

### Post by oldfred on 2012-09-22
They still have that incorrect message of install to all of them. That has created so many   issues especially with those dual booting.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

Only choose the drive that you boot from. Normally the same drive you have Ubuntu installed and only the MBR not any partitions PBR.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

