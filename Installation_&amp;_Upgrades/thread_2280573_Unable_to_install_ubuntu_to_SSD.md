---
title: "Unable to install ubuntu to SSD"
date: 2015-05-31
forum: Installation &amp; Upgrades
---

### Post by enoac on 2015-05-31
I have an Asus X551C that I am changing out the hard drive from a mechanical to a 120GB ssd,  I want to do a clean install of ubuntu 15.04.  

However when I try to install it, when I get to the section where I should be able to select the drive to install it to, nothing shows up. 

When i'm running ubuntu live from a usb I can see the drive and make changes to the format and file system.  it's only during the install process that it's unable to see the drive. 

Any suggestions?

---

### Post by oldfred on 2015-06-01
UEFI or BIOS install?

How did you partition drive?
Post this from live installer:
sudo parted -l

How you boot installer is how it installs:
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

