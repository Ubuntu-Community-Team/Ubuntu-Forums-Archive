---
title: "Upgrade hard disk procedure"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by rlovison on 2006-07-31
Hi,

I currently have Dapper installed on a 3.2GB hard drive (don't laugh) and wish to upgrade to a 20GB drive.  The 3.2GB drive is hda installed on the motherboard built-in controller.  Three other faster 133ATA drives containing Win XP Pro are installed on a PCI RAID controller.  Grub is installed on the MBR of the 3.2GB drive and the Win XP option on the menu uses map to remap the drives so I can boot Win XP from the Grub menu.  I want to copy the 3.2GB drive to the 20GB drive, reinstall Grub on the 20GB MBR and then remove the 3.2GB drive.  Can someone give me a procedure for doing so or point me to a webpage that addresses this?  The Hard drive mini HowTo provides some answers though is a bit outdated and deals with LILO.  

Thanks,
Richard

---

### Post by zxee on 2006-07-31
[http://www.linuxforums.org/forum/debian-linux-help/19007-need-help-moving-my-root-filesystem-another-partition.html](http://www.linuxforums.org/forum/debian-linux-help/19007-need-help-moving-my-root-filesystem-another-partition.html)
[http://fedoranews.org/ghenry/partition/](http://fedoranews.org/ghenry/partition/)

The above links have different styles but should get you started. As stated you will need to edit /etc/fstab and /boot/grub/menu.lst
You could also use dd from a shell to do this, check out man dd, given that you only have a 3.2gb drive to move it may not be so bad or long anyway.

---

