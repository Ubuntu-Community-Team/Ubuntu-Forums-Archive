---
title: "Grub problems when deploying clients with Systemimager"
date: 2005-08-27
forum: Installation &amp; Upgrades
---

### Post by sinbad782 on 2005-08-27
Hi All,
  I recently took delivery of three identical P3 machines to be used as client workstations in student accommodation belonging to my college. I am interested in saving time and keeping the images up to date by deployed cloned images using systemimager ([www.systemimager.org)](www.systemimager.org)), but have had a few problems using this method. 

First I prepared the golden client, ran the prepare client utility, and pulled the image via getimage onto the image server (my own personal ubuntu machine). All of these steps went perfectly. 

I made an auto install diskette using mkautoinstalldiskette and added a tweaked \local.cfg to this. My DHCP server is not on the same machine as the image server and I needed to set this in the local.cfg file. I then took this diskette and booted the first client node to be imaged with the cd and downloaded the image onto this machine. All the files seemed to copy across perfectly well.

Upon completion and trying to restart and boot the new image from the hard disk, I discovered that the grub bootloader was seemingly not present. In order to try to fix this, I booted with a Knoppix CD, mounted the filesystem as read/write, then chrooted into the captive filesystem on /mnt/hda1 and tried to do a grub-install on /dev/hda (the single hard disk).

This seemed to work, and rebooting from the hard disk brought up a grub menu etc. When the ubuntu image started to load I got a kernel panic and some messages like;

init: failed to find /dev/null: no such file
init: failed to open /dev/console

I had a look around on the systemimager mailing list archives and it looks like this is a problem with Ubuntu as this uses udev and seems to require some extra configuration of the auto install scripts. I am using systemimager 3.2.3-3 for the client and server portions. 

I eventually got the client image to boot by adding 'devfs=mount' to the kernel line in /boot/grub/menu.lst at boot time and then editing this in permanently once the machine had booted.

Has anyone else had similar problems using Systemimager? - I'm sure there's a better way of doing this than manually booting each client node using Knoppix and installing grub properly. Perhaps I'm being really stupid, and have missed out some configuration steps, and so please let me know how you yourselves have got this working!

Thanks,

Paul S.

---

### Post by IngerK on 2005-08-28
I have had the same problem, but not with systemimager. I just bought 80GB disk to my laptop and cloned the old ubuntu-partition with "dd". I had to use "devfs=mount" in grub configuration too (menu.lst).

---

### Post by sinbad782 on 2005-08-28
Very weird. I tried this again and edited the config of the /etc/systemimager/autoinstall.conf file on the golden client system so that Boel on the auto install diskette used the devfs file system. 

It did install grub properly this time, but again, I was back to getting a kernel panic at boot time as /dev/null and /dev/console were not there. The solution was again to add the parameter devfs=mount to the kernel line in /boot/grub/menu.lst.

There were a couple of other small issues with systemimager - the /etc/hosts file didn't take the hostname for the new image and I also had to manually change /etc/hostname, but otherwise the new imaged machine seems to be working fine.

I have posted a note of my experiences onto the systemimager mailing list and so hopefully the devs will figure out a way to overcome this issue for Ubuntu.

---

