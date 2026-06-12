---
title: "grub2 and initrd failed to install"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2010-05-17
I just did a new install of Ubuntu 10.04 (64 bit) on a system with multiple older versions of Ubuntu already installed. There was a dpkg error during the install with no useful information provided, otherwise the install completed normally. When I rebooted, the old grub2 ran and presented my old boot menu. When I mounted the 10.04 partition to see what was there, I found that /boot/grub/ was empty and /boot/initrd.img was missing. The other boot files were present.

So what should I do now?

thanks
Mike

---

### Post by oldfred on 2010-05-17
kanasnoob has good info on chrooting into your system:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Once chrooted into it i would run:
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

#install grub2 (this may be all you have to do, the above is just to make sure you are up to date)
apt-get install grub-pc grub-common

#and if you want to boot with grub2 on sda
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc

---

### Post by kornelix on 2010-05-18
I have been to hell and back with Ubuntu 10.04. I finally figured out that there was some kind of fatal interference with existing installations of older Ubuntu versions on the same PC. Once I deleted these, the installation of 10.04 went smoothly. I installed it 4 times before realizing this. I use the older versions to test software that I write.

A short list of things that went wrong, from faded memory:

1. 
1st attempt: no grub2 and files in /boot were not complete (missing at least initrd)

2. 
2nd attempt: fstab in 9.10 partition was written over by 10.04 install, and wrongly. I did not know how bad 9.10 was hosed so I deleted it, reinstalled it, and thought I could use its grub2 to boot 10.04. This failed, and I don't recall the details.

3. 
Installed 10.04 again and this time grub2 was installed (why the difference?). 10.04 booted but 3 other Ubuntu partitions were hosed in some obscure manner. They booted OK but login attempts failed because gnome crashed. xsession.log said that "IM" had insufficient privilege. I never used IM and I wonder if the 10.04 wonderful new social network stuff did this to me.

4.
After a little configuration work on 10.04 it failed to log in, citing unspecified gnome power management configuration errors (I had not touched this area). 

5.
I finally deleted all other partitions and installed 10.04 by itself. This worked.

So I am really disappointed with this mess. My luck with Ubuntu had been good for 3+ years. I need still to rebuild the lost Ubuntu installs, but I will use another computer for this.

---

