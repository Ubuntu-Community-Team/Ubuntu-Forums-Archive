---
title: "Ubuntu cannot be installed &amp; run smooth on ASUS K550V machine"
date: 2019-01-16
forum: Installation &amp; Upgrades
---

### Post by uezbe on 2019-01-16
Hi guys,

I really need help regarding the Ubuntu installation on ASUS K505V ([https://www.asus.com/us/Laptops/X550VX/overview/](https://www.asus.com/us/Laptops/X550VX/overview/)).
I had installed Windows 10 Pro and want to install Ubuntu 16.04 or 18.04 on dual boot but the Ubuntu system is crashed.

Someone experienced similar issues or have some ideas what could be?
The installation from a bootable USB drive is running so slow especially on the parts when the partitions have to be listed.

After installation, it does not run smooth. 
It's kind of broken and it's not opening browser or sometimes other programmes.

My machine specifications are:
[COLOR=#333333][FONT=&amp]Memory: DDR4 2133 MHz SDRAM, OnBoard Memory 4 GB / 8 GB, 1x DIMM socket, DIMM Up to 16 GB
Graphic: [/FONT][/COLOR]NVIDIA® GeForce® GTX 950M
Interface:
[LIST]
[*]1 x COMBO audio jack
[*]1 x VGA port/Mini D-sub 15-pin for external monitor
[*]2 x Type A USB3.0 (USB3.1 GEN1)
[*]1 x USB 2.0 port(s)
[*]1 x RJ45 LAN Jack for LAN insert
[*]1 x HDMI
[/LIST]
CPU: i7-7700HQ

After a restart, there is infinite message running on the screen like Mining OS PCIe Bus Error (ex. [https://www.youtube.com/watch?v=rGxZ3W9eLfo](https://www.youtube.com/watch?v=rGxZ3W9eLfo))

I would really appreciate and be very thankful if you guys help me find a solution to this issue.

Best,
Kire

---

### Post by howefield on 2019-02-06
Thread moved to the "*Installation & Upgrades*" forum.

---

### Post by oldfred on 2019-02-06
Partition scan is often slow. But if issues it may not ever stop.
Most often the issue is Windows 10 fast start up is on. Then the Linux NTFS driver cannot see the NTFS partition.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Have you updated UEFI from Asus? And if SSD, updated firmware?
Many Asus models need boot parameter. And if nVidia, you will need nomodeset boot parameter to boot live installer and first boot of install or until you install nVidia driver from Ubuntu repository.

If fast start up is off run this from live installer's terminal:
sudo parted -l
sudo fdisk -lu
 
Issues are often common across many models by brand. Bigger differences if Intel or AMD based.

 How to install Ubuntu on ASUS F556U, JournalError error?  add pci=nomsi 
[https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221](https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221) 
      
 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
ASUS X540U pci=noaer instead of pci=nomsi and it also worked
[https://ubuntuforums.org/showthread.php?t=2391201](https://ubuntuforums.org/showthread.php?t=2391201)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[URL="https://ubuntuforums.org/showthread.php?t=2327570"]https://ubuntuforums.org/showthread.php?t=2327570

      [/URL]
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 
    [URL="https://ubuntuforums.org/showthread.php?t=2327570"]
[/URL]

---

