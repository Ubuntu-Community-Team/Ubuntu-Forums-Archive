---
title: "Partition Problem"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by wiseguy1515 on 2007-10-26
I'm trying to install ubuntu alongside windows, so I need to partition my hard drive. However, when I try to do this it does not give me the option of a guided install and does not let me chose my partition size.
Can anyone help?
I'm using an HP Pavilion dv8000 laptop, and I want to set of about 10 gigs for Ubuntu.
Thanks!

---

### Post by It_Was_Luck on 2007-10-26
I am currently doing the same thing... You will have to do it manually.

Once you select manual you'll need to partition your main NFTS drive to take 10GB off of it, once you do that create a 9GB ext3 file with the mouse point "/" This is where ubuntu will go, then using your remaining 1GB create another file, expect make this one a swap file, and with no mouse point.

Ubuntu will then be installed with grub, then once you power off and back on grub will come up asking you to boot to windows or ubuntu.

hth

---

### Post by Pumalite on 2007-10-26
If Vista; use the Vista partitioner to allocate space for Ubuntu.
Then use Gparted Live CD and prepare your partitions:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for /home
Then use the partitions you made during the installation.
I would use Alternate CD, but you can go 'Manual' in the Live CD
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

