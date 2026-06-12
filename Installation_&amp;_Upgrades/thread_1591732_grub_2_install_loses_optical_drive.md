---
title: "grub 2 install loses optical drive"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by owlmonkey on 2010-10-09
I recently partitioned my hard-drive to dual boot Windows 7 and Ubuntu 10.04 LTS. It wasn't until I finished everything and got grub working to do the dual boot that I noticed that although I could still boot off my live Ubuntu CD I could not see the device in either Windows or Ubuntu. As I wasn't sure where the problem arose I started down various blind alleys such as Windows Troubleshooter and 'Scan for Hardware Changes' in Window's Device Manager. After this I reinstalled Ubuntu (problem remained), then reinstalled Windows at which point, although I didn't have dual boot as yet (had not re-installed grub) Windows was picking up my DVD/CD drive. As soon as I reinstalled Grub 2 (as per ) I lost my device from Windows, and it was also not picked up when I booted into Ubuntu. I was still able to boot off the live CD and it was present there as /dev/sr0 (and various aliases pointing to sr0), but there is no sr0 in /dev when I boot off the installed Ubuntu.

I am on a Toshiba laptop (Satelite A100), running Windows 7 Professional 323 bit on the first main partition and Ubuntu 10.04 LTS on the second. My DVD drive is a Panasonic UJ-820B DVDR. 

This is not an intermittent problem like in the post [http://ubuntuforums.org/showthread.php?t=1565893&highlight=grub2+dvd+drive](http://ubuntuforums.org/showthread.php?t=1565893&highlight=grub2+dvd+drive)

---

