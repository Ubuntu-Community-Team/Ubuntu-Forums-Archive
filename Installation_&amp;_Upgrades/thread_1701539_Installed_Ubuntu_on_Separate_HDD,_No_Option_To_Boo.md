---
title: "Installed Ubuntu on Separate HDD, No Option To Boot."
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by Dice62 on 2011-03-06
Hello,

I tried Ubuntu 10.10, and the Live CD works, and I installed it also via Wubi. The 30gb was limiting, as I used it for media, such as tv shows, and movies that are of blu-ray quality, so the 30gb couldn't support these big files.

This led me to install a new 500gb hard drive to do a fresh install of Ubuntu on, to use the whole drive. It installed fine, and after installation, it said to restart the computer in order to use the installation, and also to remove the CD and press enter. So I did all the above, but it booted straight into Windows 7. When I had the Wubi install, it asked which to boot into, and when I installed Ubuntu before, it usually asked me which I wanted to boot into, through Grub I believe.

Now I get no options and it boots straight into Windows 7 on a restart. 

How can I install Grub in order to access Ubuntu, if that's the reason?

Can I just add Ubuntu to the regular windows bootloader like how Wubi had it, or is Grub a necessity?

I have 3 hard drives in my pc:
 - 250gb drive which windows 7 is installed (C and D partitions)
 - 500gb drive on which I have my windows 7 media files (E partition)
 - 500gb drive on which I installed Ubuntu 10.10 on

Through Administrative Tools > Computer Management > I can see the drive Ubuntu was installed on, labeled Disk 1, a healthy primary partition, but I cannot see it under My Computer, of course.

How should I proceed?
Thanks again for your time.

---

### Post by ubfan1 on 2011-03-06
Grub was probably installed on the 500G disk, but you need to go into your BIOS (check the messages at boot up for the key to hit e.g. f10) and move the 500 disk to the top of the boot order.

---

