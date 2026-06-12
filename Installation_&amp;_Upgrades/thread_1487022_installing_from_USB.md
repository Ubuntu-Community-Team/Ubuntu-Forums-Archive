---
title: "installing from USB"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by stork123 on 2010-05-18
I am considering buying a netbook and installing the netbook remix from a bootable USB. During the installation, does the installer give me the option to create a dual boot scenario and keep the windows 7 as a partition? If it does not, what is the best way to clone the windows 7 install and can I put it on a usb to boot and install from in the future?
Thanks!

Christopher
Happy (desktop) ubuntu user.

---

### Post by darkod on 2010-05-18
Yes, the netbook remix is giving you the same options during install. If you need to shrink the win7 system partition to make space, use the windows Disk Management. Then reboot few times so win7 can do the disk checks.
Only then proceed with installing UNR.

If this is your first touch with UNR I also suggest to run it in live mode first. That can show you any hardware issues, and also you will be able to see if you like the layout because it's different from the desktop version. At least for UNR 9.10 it was.

For my netbook I immediately went with UNR 9.10 without checking it out first, but I preferred how the desktop version looks so after two days I had to reinstall over it. :) The desktop version is working just fine on netbooks, in case you are worried about that.

PS. Having a backup of windows never hurts. You can check the Backup & Restore tool in win7. It can save image on ext hdd. It can also create startup cd image, but not sure how to make bootable usb from that because you don't have cd-rom to use a startup win7 cd.

---

### Post by stork123 on 2010-05-18
Great! Thanks for the reply.
I am looking at buying an Asus EE PC 1005HA off a guy.

---

### Post by libssd on 2010-05-18
> **darkod said:**
> Yes, the netbook remix is giving you the same options during install. If you need to shrink the win7 system partition to make space, use the windows Disk Management. Then reboot few times so win7 can do the disk checks.
Only then proceed with installing UNR.

If this is your first touch with UNR I also suggest to run it in live mode first. That can show you any hardware issues, and also you will be able to see if you like the layout because it's different from the desktop version. At least for UNR 9.10 it was.

For my netbook I immediately went with UNR 9.10 without checking it out first, but I preferred how the desktop version looks so after two days I had to reinstall over it. :) The desktop version is working just fine on netbooks, in case you are worried about that.

PS. Having a backup of windows never hurts. You can check the Backup & Restore tool in win7. It can save image on ext hdd. It can also create startup cd image, but not sure how to make bootable usb from that because you don't have cd-rom to use a startup win7 cd.
If it's accessible, remove the HDD, then install from a USB stick to a memory card, if your netbook is capable of booting from one. I did this multiple times (trying out different formatting options, Ubuntu, Kubuntu, Xubuntu, netbook remix, etc.) before screwing up the courage to do a permanent install in a 32gb partition. 

**VERY IMPORTANT**: Read *[Ubuntu Pocket Guide and Reference]("http://www.ubuntupocketguide.com/index_main.html")*, by Keir Thomas before doing anything. Run chkdsk and defrag hard disk before partitioning. And, of course, be **sure** you can restore Windows if something goes wrong.:P

---

### Post by wilee-nilee on 2010-05-18
> **stork123 said:**
> Great! Thanks for the reply.
I am looking at buying an Asus EE PC 1005HA off a guy.

IF the guy doesn't have the install DVD, have them get it. especially if it is a OEM so that you have everything covered. If it is a regular install, you can get the key read by this.
[http://www.magicaljellybean.com/keyfinder/](http://www.magicaljellybean.com/keyfinder/)
The key in a oem is not usable, and the oem install disks auto activate, but a install doesn't. 

I would also confirm that W7 is a legitimate copy, not a cracked version. This model comes with W7 now but the originals didn't, and is still sold without it, also make sure the ram is 2 gigs.

---

