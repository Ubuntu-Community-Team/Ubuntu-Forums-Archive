---
title: "Upgrading from Dapper to Fiesty by using PartImage"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by space_boy on 2007-05-02
I currently an using Dapper and have Fiesty running in a test partition. I want to replace Dapper with Fiesty but do not want to go through a new installation of Fiesty. If I create a backup image of Fiesty with PartImage, can I the perform a restoral and place it over the Dapper in its partition? What changes will I need to make to my GRUB to allow Fiesty to boot from its new partition location?

---

### Post by aysiu on 2007-05-02
Why not [reinstall Grub to the MBR](http://ubuntuforums.org/showthread.php?t=224351) and just be sure to use Feisty's /boot/grub/menu.lst instead of Dapper's? A lot less messy.

You can then--once you've successfully booted into Feisty with the new Grub--delete the Dapper partition and use it as extra data space.

---

### Post by space_boy on 2007-05-02
Will this work with Fiesty not operating from the first main partition of the hard drive? I am planning on creating a separate /home partition with the home folders from Dapper, so I want to move Fiesty to hdc1 of my hard drive.

---

