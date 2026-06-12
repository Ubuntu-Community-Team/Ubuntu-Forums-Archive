---
title: "[wubi] Installed 12.10 in WinXP SP3 and don't get the option to boot Ubuntu"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by Gasman on 2013-01-26
I did a fresh installation of XP SP3 on an IBM ThinkPad T40, 512 MB of RAM, Pentium M 1.5 GHz processor. I ran the wubi executable for 12.10 and let it download and unpack the image. When it said I needed to reboot the computer to complete the installation, I let Wubi restart it. During the reboot, it never came up to the boot menu and just booted into windows.

When I check the Startup Options in System Properties and choose the option to edit the Boot.ini from there, I found this:

[B][operating systems]  
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn  
[boot loader]  
timeout=5  
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS[/B]

I thought there might have been a problem with the .iso that Wubi pulled down, so I manually downloaded the .iso and put it in the same folder as Wubi and ran the installation again with the same results after the reboot.

I had previously installed Lucid on this machine before deciding to reinstall XP and use Wubi to dual boot the latest and greatest version. 

Any ideas? I've used Wubi on other laptops with no problems.

---

