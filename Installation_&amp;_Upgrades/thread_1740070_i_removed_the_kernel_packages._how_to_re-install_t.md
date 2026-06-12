---
title: "i removed the kernel packages. how to re-install them"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2011-04-26
I removed the linux-image-2.6.32-31-generic package (and all the older ones)
from my 64-bit Lucid Lynx machine.

When I boot up, the grub menu only has memtest as a choice.

I am able to boot the machine with the LiveCD and can mount the drive.
(look like it's read only mode right now.)

But now, how do I reinstall the linux-image-2.6.32-31-generic package
(or any package for that matter) onto the disk partition that represents the machine?

---

### Post by oldfred on 2011-04-26
You can chroot from your liveCD to your non-working system and then run updates.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
kansasnoob- full chroot one line version with &&----
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)


#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
Commands once in chroot:
if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
#if grub is ok
sudo update-grub
#otherwise as posted in the chroot methods by drs305 reinstall grub & reinstall the grub bootloader to the MBR.

---

### Post by gmoore777 on 2011-04-26
thank you.

finding various information, this was my solution:
(and this is a Linux virtual machine running under VMware Player
on a 64-bit Windows 7 machine)


I inadvertantly `sudo apt-get purge linux-image-2.6.32-31-generic` the only image on
an Ubuntu Linux VM machine.

On boot up, only memtest was on the grub menu. Doh!

Solution:
To boot from the LiveCD after a virtual machine already installed with an OS, on starting the machine, must click mouse in the window, and hit <ESC> to get a small 2” x 1” boot menu. Although you will see this window, it starts booting the GRUB menu immediately.

Hitting <F2> and clicking mouse got me into the BIOS menu, where I could then move the CD Drive as first in line for the boot choices.

Once the LiveCD is booted and running Linux:
	sudo su
	mkdir /mnt/temp
        mount /dev/sda2 /mnt/dev
        chroot /mnt/dev
        apt-get update; apt-get install --reinstall linux-generic    
  # this meta package, linux-generic    will pull in all dependent packages
	    can not write log, openpty() failed. (/dev/pts not mounted)?
	    other errors about /proc/… and /dev/…

To solve the failed install, in another window:
	sudo su
        mount -o bind /dev /mnt/temp/dev
        mount -t proc none /mnt/temp/proc
Then retry the apt-get above.

Success!!

---

