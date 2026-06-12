---
title: "Installation Issues"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Clayton00 on 2008-02-26
Installation Issue.

Gutsy, I got it to install once. The other installation tries; my monitor was saying out of range and kicking off. The one time I did go thru the installation process, after installation, I rebooted, GRUB error 21. Then I could not boot into anything.

Used Super Grub, was able to boot back into Windows, but could not boot in to Ubuntu Gutsy.

Down loaded Hardy Alpha 5 release. Same video issues, but able to install in safe graphics mode. Upon reboot after installation, grub error 21. selected disk does not exist.
Again used S grub to try to repair/boot into Hardy. I did get the option to select the 3 boot options for hardy, generic, recovery, memtest. Again GRUB error 21.

My System Info:

I feel my setup may have something to do with my issue. If it is, I do not know how to overcome it.
HARDWARE:
Core 2 Quad 2.4GHZ
Intel DX38BT motherboard
MSI NX8600GT Graphics Card
2 GB Team Extreme DDR 3, 1066 , CL 7-7-7-21
2 Asus DVD burners SATA
3 SATA WD Hard drives
550 Watt Power Supply

Vista Home Premium 32 Bit

Vista is installed on a SATA raid Array, I am not trying to install Ubuntu on a raid.

I have a separate 500 GB HD, SATA, 3 partitions, one 160 GB NTFS, 2 GB Swap, and the rest as the drive to install on, /, ext3.

Question? Does having Vista on a raid somehow interfere with GRUB?
I just built this computer, and any suggestions on how to get Ububtu installed would be great.

Thanks
Clayton

---

### Post by Pumalite on 2008-02-26
You are going to have problems because Grub will try to install to MBR, which is your Raid and it will fail. You might as well install Grub to the drive you are installing Ubuntu and later booting Ubuntu with Super Grub or changing the order of boot in BIOS.

---

### Post by Pumalite on 2008-02-26
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

