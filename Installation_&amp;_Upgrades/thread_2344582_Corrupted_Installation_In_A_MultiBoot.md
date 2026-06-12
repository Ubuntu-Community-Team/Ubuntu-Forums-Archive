---
title: "Corrupted Installation In A MultiBoot"
date: 2016-11-26
forum: Installation &amp; Upgrades
---

### Post by carlmacgentey on 2016-11-26
I&#8217;m running Windows XP Pro and Ubuntu 16.04 LTS on an old Hewlett Packard laptop with a BIOS. I made a mistake while trying to install Kali Linux to an external hard drive. 
  
  When I select Windows from the GRUB menu I get offered the alternatives of: (1) booting into Windows XP Pro or (2) continuing on with a debian installation. 
  
  Worse, gparted (in Ubuntu) now shows a 50 GB extended partition (empty) labeled /dev/sda2. I am leery about deleting this partition as I think I will lose two sub-partitions along with it: /dev/sda5 ext4 and /dev/sda6 Linux-swap.
  
  Even more worse, I cannot update my software in Ubuntu. I keep getting error messages about being unable to update grub-pc. Advice? Suggestions? Comments?

---

### Post by lisati on 2016-11-26
Duplicate of [https://ubuntuforums.org/showthread.php?t=2344581](https://ubuntuforums.org/showthread.php?t=2344581)

---

