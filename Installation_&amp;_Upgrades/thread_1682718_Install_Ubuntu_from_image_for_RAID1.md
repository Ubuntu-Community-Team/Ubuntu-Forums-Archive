---
title: "Install Ubuntu from image for RAID1"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by dog6284 on 2011-02-06
Hello,
I am in the process of switching over from an old web server to a new one. 
I hope to create an image of my existing Ubuntu server HDD, which is a single physical drive with one partition (not RAID).  My new server will use hardware-based RAID-1.

Question: Is is possible to use the single drive image and convert to RAID?  Or, is it neccesary to do a clean install, and proceed to setup RAID during the installation?

---

### Post by ronparent on 2011-02-06
Most likely yes if you copy the image of your existing server to the raid drive already running as a raid. The image will be automatically mirrored as copied. You will have to install the raid driver to that new install. Also the copy if a direct copy of the original partition with the same uuid will not require editing of /etc/fstab. Otherwise that and other fixable problems would ensue.

Where grub is installed depends on the flavor of the raid and whether it permits booting from the raid. If both installs have the same uuid it would be best to disconnect one to avoid a situation where you don't know which is booted.

---

