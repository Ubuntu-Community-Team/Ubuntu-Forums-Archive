---
title: "Help getting Ubuntu install on external HDD working! (used guide)"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by mrsack on 2008-03-24
Thanks for the external hdd guide [(here)!]("http://ubuntuforums.org/showthread.php?t=678146") I followed it all the way, but I can't get Linux to boot at all. I have Vista installed on my internal HDD and then Ubuntu on the 2nd partition of my 500GB MyBook.

I think the problem lies with my pc not booting from my external. I have "removable drive" as my 1st boot option on my bios (p5b-e) but it won't boot even with all other options disabled. I have 3 guesses as to what the problem is:

1. During the partitioning during the install, I noticed the "flag as bootable" or whatever option for my root partition. The guide didn't say anything about checking this, so I left it alone. Should I have?
'
2. When editing the grub list, there were only two locations where a "(hdx,y)" was located. I think they were both (hd1,1) so I changed both to (hd0,0). I'll try to fire up a live CD to try to check that file out again. (I have since done went back and thought I fixed it, which is the attached menu.txt file)

3. Maybe my bios has a problem booting from a usb hdd? Is there an easy way to tell? (maybe some small test program i can put on my external that will boot and display something on my screen)

I have attached copies of the modules and menu list, so hopefully that will help you help me :)

Any help would be appreciated!

---

### Post by Amarsingh0793 on 2008-04-04
Check the boot order in your BIOS Configuration. Make sure booting from usb is before the hard disk.

---

### Post by dstew on 2008-04-04
Did you install the grub boot loader to the MBR of the external drive during the installation process? I bet your motherboard can boot the external drive, so if it doesn't boot, it probably does not have the grub boot loader on it. Do you remember where you installed grub?

Ubuntu doesn't care about the bootable flag, but your BIOS might. Some BIOSes can boot partitions, as well as disks. But, most of the time it doesn't matter.

---

