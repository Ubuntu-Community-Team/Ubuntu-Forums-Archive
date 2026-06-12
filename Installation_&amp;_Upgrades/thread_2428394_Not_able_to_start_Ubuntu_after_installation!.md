---
title: "Not able to start Ubuntu after installation!"
date: 2019-10-03
forum: Installation &amp; Upgrades
---

### Post by ricc91 on 2019-10-03
Dear all, 

I am trying to install the Ubuntu 18.04 on a machine but although the installation procedure is finished successfully, when I restart the computer I get a black screen with a fixed blinking pointer and I cannot do anything but restarting the computer.
I have a very little knowledge about these things but it seems that I am not able to boot correctly the partition where I have installed the OS. Giving a look around a possible solution was to use the Grub menu that I am not able to see. So I installed through the Live Session of Ubuntu (booted from USB) this boot-repair tool. With this I reinstalled Grub and I checked that the tool would really restart on the partition (/dev/sda1 in my case) where I had previously installed Ubuntu. By the way, once this was done boot-repair recommended to restart the computer but after doing so I got again my black screen with no track of Ubuntu. I also checked in the BIOS that the HDD had the highest Boot Priority... So reached this point I have really no idea! Thanks in advance for your help!

This is the result of the boot-repair tool in case you need: [http://paste.ubuntu.com/p/s2bvZvNkhQ/](http://paste.ubuntu.com/p/s2bvZvNkhQ/)

Thanks!

---

### Post by ricc91 on 2019-10-03
Solved!

Same problem here: [https://ubuntuforums.org/showthread.php?t=1745247](https://ubuntuforums.org/showthread.php?t=1745247)
I just followed the instructions and it worked.

---

