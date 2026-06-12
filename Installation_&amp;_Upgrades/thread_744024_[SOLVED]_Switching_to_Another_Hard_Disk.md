---
title: "[SOLVED] Switching to Another Hard Disk"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by ene_dene on 2008-04-03
Here is my problem. I decided to try Linux 2 months ago, and I installed Ubuntu, and than I installed Fedora on same hard drive. On first partition I have winXP. So since I put Fedora last, it's boot loader (grub) gives me a choice which OS should I run.
I liked Ubuntu from the start and I don't use and other systems anymore, so I'd like to delete Windows and Fedora, reformat my drive so that I can put Ubuntu on first partition and the rest I'll divide in some other way, which is not really important.
What I want to do is to copy this all the settings, programs, updates, licences (I installed lot of stuff, don't want to go through that again!) to that future first partition and that boot loader starts Ubuntu. Is there some way to do this?

---

### Post by chewearn on 2008-04-04
1. Back-up all important stuffs you can't afford to loose.

2. Download a partition tool and burn to disc; I usually use Gparted livecd:
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

3. Shutdown, plug-in both harddisks.

4. Boot into the Gparted livecd.

5. Clone the ubuntu partition, by right-click on it, select copy.  Then, in the new HD, right-click select paste.  Click apply to commit the change.

6. Create an extended partition on the new HD, and create a swap partition within the extended partition.

7. Repair grub; follow this link (you need to read it entirely, and choose the appropriate method):
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

8. Edit /etc/fstab; fix UUID of the swap partition to match the newly created one

---

### Post by ene_dene on 2008-04-04
Thanks!

---

