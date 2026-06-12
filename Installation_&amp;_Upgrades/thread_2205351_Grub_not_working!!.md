---
title: "Grub not working!!"
date: 2014-02-13
forum: Installation &amp; Upgrades
---

### Post by Loreta on 2014-02-13
Hi!! I installed ubuntu 12.04 along with windows, but then I needed to use a special program in scientific linux (SL6), so I used gparted to "erase" the windows partition, and it appeared as unallocated memory. Well, via cd I installed the last release of scientific linux, and when it asked whhich type of installation I wanted, I tried to make the "use free space" from the windows unallocated memory. It did not work, so chose the "shink the current system". 

From then on, I just made next>next>next.... And installed normally the SCL6. 

The problem is that, once I get out of SCL6, I can't get back to ubuntu, and appears the boot of windows or SCL6. Dunno what to do. 

This is the distribution of my system is in the attachment.



It's made all a mess... I have unallocated memory everywhere and the partition of SCL almost got none memory.

I really don't want to install once more SCL because I already installed what I need, no problem to go back and install ubuntu, actually I would like the last release.

Thanks

---

### Post by oldfred on 2014-02-13
Better to just copy text to reply. If longer text use code tags to preserve formatting. Easy to add with # in advanced reply. 
It looks like you have LVM or encryption with LVM? You cannot use gparted on LVM partitioning but have to use LVM tools to resize LVM.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[URL="http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html"]http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html

[/URL] Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

[URL="http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html"]
[/URL]

---

