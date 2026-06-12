---
title: "Grub loading error"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by AmbiguousOutlier on 2010-02-05
I've been trying for the last couple of weeks to get my xbmc live installation working on my HTPC with little success. So today I decided I'd dual boot ubuntu with xbmc live. 

I wiped my hard drives and set up partitions like so;

Ubuntu 9.10:

sdb1 hardware RAID 1 setup on 2x 1tb disks ext4 mounted /media/library
sdc1 15gb primary ext4 mounted /
sdc2 15gb primary ext4 mounted /media/xbmc
sdc3 4gb primary swap
sdc4 460gb primary ext4 mounted /home

XBMC Live:

sdb1 hardware RAID 1 setup on 2x 1tb disks ext4 mounted /media/library
sdc1 15gb primary ext4 mounted /media/ubuntu
sdc2 15gb primary ext4 mounted /
sdc3 4gb primary swap
sdc4 460gb primary ext4 mounted /home


First of all I installed Ubuntu on sdc2 (I wanted xbmc to be first on the disk 'cause I thought it might boot quicker) But I got a grub loading error 15. So I assumed it was because I didn't have anything on sdc1. So I re-installed Ubuntu on sdc1 formating sdc2. However I got the same error. I googled it and came back with a similar solution to this;

[http://ubuntuforums.org/showthread.php?t=43591](http://ubuntuforums.org/showthread.php?t=43591)

I can't find the exact thread but I followed similar instructions. However after booting into the live disc and doing the steps in the thread, it told me /boot/grub/stage1 does not exist.

So I thought I'd just go ahead and install XBMC Live in the hope that would fix it. It did not.

I'm still getting an error 15. And I'm not sure what to do. Please help.

EDIT: I read something to do with Grub not working with ext4 so I tried re-installing again with the same setup as above but with ext3 on all sdc partitions, still does not work. Same error 15 as before.

EDIT: I tried re-installing ubuntu using the automated method and using the entire disk. But I still the same error 15.

EDIT: OK now I've decided it could be a problem to do with my RAID. So I unplugged it and connected it up on SATA2 and SATA3 on the mobo. Then plugged my os drive and bd drive into SATA0 and SATA1 respectively. Then did a clean install of ubuntu again with the following setup;


Ubuntu 9.10:

sda1 15gb primary ext4 mounted /media/xbmc
sda2 15gb primary ext4 mounted /
sda3 8gb primary swap
sda4 460gb primary ext4 mounted /home
sdc1 hardware RAID 1 setup on 2x 1tb disks ext4 mounted /media/library

Still wouldn't boot, but this time came up with grub rescue>

So I decided to install XBMC Live in the hope that would fix the problem using the following configuration;

XBMC Live:

sda1 15gb primary ext4 mounted /
sda2 15gb primary ext4 mounted /media/ubuntu
sda3 8gb primary swap
sda4 460gb primary ext4 mounted /home
sdc1 hardware RAID 1 setup on 2x 1tb disks ext4 mounted /media/library

Managed to boot into xbmc fine, then I rebooted pressed esc at the grub menu and booted into Ubuntu. There all I did was activate the open source GPU drivers and ran the update manager. When I rebooted all I get is this;

```

GRUB loading.
error: no such disk
grub rescue>

```

I've researched grub rescue and all of the commands they tell me I can use don't work. It just says unknown command.

---

