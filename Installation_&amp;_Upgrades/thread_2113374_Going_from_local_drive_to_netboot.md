---
title: "Going from local drive to netboot"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by bengsig on 2013-02-07
I wanted to switch my fully functional 10.04 install from running off a hard drive to boot via pxe and run with everything NFS mounted from my NAS.  

These are some tips that may help others achieve the same.

First, I more or less followed

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

My NAS already was running nfs server but did not have tftp server, so I installed tftpd-hpa on it.

Bootp was already available on my router (running dnsmasq in a build from dd-wrt.com), and all I had to do there was to add this extra dnsmasq option:

dhcp-boot=/pxelinux.0,nameofmynas,192.168.x.x

x.x really being the IP of my NAS.

On [http://www.syslinux.org/wiki/index.php/PXELINUX](http://www.syslinux.org/wiki/index.php/PXELINUX), I found important information on how to setup the tftp server including naming convention for files/directories.  

When creating the initrd.img file (see the first link above), it is important to follow the instructions on including the necessary network module for the card on your system.  As I already had a fully running Ubuntu (I just wanted to get rid of the harddisk), I could find the module necessary easily.  

I used somewhat different steps in copying the vmlinuz and initrd.img files; the result must be that they have to reside where they can be retrieved via tftp during pxe boot.

Still running the hard-disk based system, I made a brute-force copy of everything (except things with special mounts such as /dev, /proc, etc) from the hard-disk to the place on my NFS that later will become the root of the pxe booted system.  The mount points for the special directories (such as /dev, /proc) must exist and be empty.

At this point, I changed the BIOS of my Ubuntu box and was able to reboot using pxe.  Most appeared to work, the system would come up with nfs, but the graphical interface (gdm with X) did NOT start properly.  Effects were very similar to those described in [http://ubuntuforums.org/showthread.php?t=980711](http://ubuntuforums.org/showthread.php?t=980711) and the solution for me was to remove and reinstall ubuntu-desktop and gnome-power-manager using

apt-get remove ubuntu-desktop gnome-power-manager
apt-get install ubuntu-desktop gnome-power-manager

I also had the issue with the wrong permission on /tmp, but fixing that did not (appear to) resolve the problems.

If somebody have read this far, I'd like to finish with a question:

Whenever there is an update to the kernel, how do I get it installed?  It is no longer simply stored in /boot, but on the NAS under the tftp server.

---

