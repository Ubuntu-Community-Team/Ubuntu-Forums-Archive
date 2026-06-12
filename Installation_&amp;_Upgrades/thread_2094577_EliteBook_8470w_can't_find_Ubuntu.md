---
title: "EliteBook 8470w can't find Ubuntu"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by Slugbreath on 2012-12-14
Hello!

I have recently got a brand new HP EliteBook Mobile Workstation 8470w for work. It came with Windows 7 preloaded, but my plan was to format the HD and install Ubuntu 12.04 in its place and then reinstall Windows 7 inside VirtualBox. (Since I will only need Windows for very few things.)

However, I seemed to have managed to mess a few things up. The 8470w comes with two hard drives. One 750 GB HDD and one 24 GB SSD. At first I couldn't find sda, that is the HDD, but only sdb. Before I followed the advice of _[this thread]("http://ubuntuforums.org/showthread.php?t=1883583")_, I formatted sdb to ext4 instead of ntsf as it previously was. I guess that this might have been a mistake since I take that that partition was probably where the MBR was. (Or am I mistaken?)

Anyhow, after running the ```
sudo dmraid -E -r /dev/sda
``` I could install Ubuntu 12.04 64-bit on sda. I got no error messages during installation.

Once installation was done, I rebooted the computer but got an error message stating:

> BootDevice Not Found
Please install an operating system on your hard disk.
Hard Disk - (3F0)
F2 System Diagnostics
Fore more infiormation, please visit: [www.hp.com\go\techcenter\startup](www.hp.com\go\techcenter\startup)

This confuses me as I did partition sda into the following:
primary ext2: /boot
logical ext4: /swap
logical ext4: /
logical ext4: /home

Any ideas on how to get this to work? Thank you in advance. I have no data on the computer yet since it is brand new, so I have no problems with doing a clean install if needed. I just don't know how to resolve this issue.

With regards
/Slug

---

### Post by Slugbreath on 2012-12-14
**_UPDATE_**
I reinstalled Ubuntu, this time placing / and /boot on the SSD and /home and /swap on the HDD. I got an error stating that > "An error occurred while restoring previously-installed applications.  The installation will continue, but you may have to manually reinstall some applications after the computer reboots."

I rebooted and got the same error as previously. I tried using _[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")_ and it gave me an URL to remember, which is as follows: [http://paste.ubuntu.com/1436537/](http://paste.ubuntu.com/1436537/)

Now when I reboot I am instead faced by the following error message:
> error: no such device: d1878ebe-1951-4f5a-818a-319265de1c88
grub rescue>

As you might notice, I really don't know what I am doing! I would really appretiate help.

/Slug

---

