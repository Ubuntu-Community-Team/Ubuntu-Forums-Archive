---
title: "Install to LVM partition and no GRUB"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by julianr on 2008-02-07
Hi all

After several years of using Fedora, I want to install Ubuntu 7.10 to an LVM partition on my AMD64 system that already has WinXP on one disk and Fedora 6 on a second disk.  I shall be installing Ubuntu on to the second disk alongside Fedora.  It's a family PC - I really can't afford to mess it up!

I understand how to use the LiveCD to install to LVM by installing lvm2 into the LiveCD system, modprobe dm-mod, complete the install and then mounting /target/boot and chroot to install lvm2 to the new system.

What I don't want to do is mess up the existing GRUB; I use bootpart from WinXP to get to Linux as it leaves the MBR of my Windows disk untouched.  I understand GRUB syntax so I'm happy to write the Ubuntu stanza into Fedora's /boot/grub/grub.conf so ideally I want the option of either not installing GRUB at all from Ubuntu or installing it in the first sector of the LVM / partition of Ubuntu - can I do that and do I have to use the Alternate CD to get that option?

Research in these forums and elsewhere suggests it's not a good idea to share /boot as it can cause problems when the distros upgrade their kernels.  But if I am using Fedora's GRUB, do I need to make Ubuntu's /boot a separate non-LVM partition?  Can I put it in the LVM volume that carries Ubuntu's / filesystem because presumably the reason /boot usually needs to be a non-LVM partition is so GRUB can load its later stages?  Or does /boot have to be regular partition for the kernel to load?

Browsing these forums has been a pleasure - everyone is really helpful.  Any help and advice really appreciated.

Cheers

JulianR

---

### Post by Fire_Chief on 2008-02-07
Any /boot partition (on any distro) cannot be on an LVM partition. It must reside on a standard ext3 partition (or other compatible filesystem type) to properly boot the OS. Also, you do need to keep a separate /boot for Fedora and Ubuntu (seems redundant but important).
You should be able to tell Ubuntu not to install a bootloader at all. After the install finishes, modify the Grub menu in Fedora to boot Ubuntu also.

Good luck!

---

### Post by julianr on 2008-02-08
Thanks Fire_Chief.  It's as I thought.  OK, here goes......

---

### Post by julianr on 2008-02-08
That has to be the cleanest, simplest install I've ever done.  Posting this from my new Ubuntu system!

This proved to be a very useful site - a really excellent walk-through for the Alternate CD:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I used the Alternate CD; everything went very smoothly and in the end I installed GRUB on the Ubuntu /boot partition so I could use the configfile grub command to get to it from my Fedora grub menu.  GRUB got the disk identities wrong (hd0 instead of hd1) - but I've been used to that because Fedora does too (it's the way my BIOS is set up to boot from the Windows SATA disk first) so that was a simple edit.

I even took my life in my hands and did the install without first unplugging my Windows disk!

So many thanks to the Ubunutu team for a great distro!  :p

One query: the Installer put an entry into Ubuntu's menu.lst for the Recovery partition of my Windows disk and an entry for it in /etc/fstab.  Not a problem, but I wonder if it is really necessary as it might confuse less computer-savvy folk?

JulianR

---

### Post by Fire_Chief on 2008-02-27
Sorry for the late reply. You may have already answered this question.

You can safely comment out the sections for the recovery partition from the Grub menu.lst and from fstab so that it does not show up on the system.

---

