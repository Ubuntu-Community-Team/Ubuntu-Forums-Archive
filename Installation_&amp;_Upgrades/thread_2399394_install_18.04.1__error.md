---
title: "install 18.04.1 ??? error"
date: 2018-08-24
forum: Installation &amp; Upgrades
---

### Post by Pein1911 on 2018-08-24
Today I try new install 18.04.1 from Usb to my HDD but it stuck at "Update and other software" window, a pop up show "??? ???" symbols after couple minutes i pressed Continue button, then cursor just show loading forever, didnt go to next step. anyone can help me ?

http://i.imgur.com/mhApTYL.jpg

---

### Post by oldfred on 2018-08-24
Moved to your own thread as thread you posted in was [Solved], so few will look at it.

What brand/model system? What video card/chip?
UEFI or BIOS system?
Windows pre-installed will be UEFI.

Can you boot to live installer mode to test system?
Have you turned off fast start up in Windows?
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Have you fully backed up system?
Did you verify ISO download? And what type of installer did you use to create installer flash drive?
       
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
    
If UEFI see general instructions in link in my signature.

---

### Post by Pein1911 on 2018-08-24
More info, my system: Main Asus z170m, cpu i5 6600k, vga Nvidia 970GTX. Yes my system all boot with UEFI, Bios fast boot Off, Windows 10 preinstalled into a SSD. Now i want install Ubuntu to a other HDD. I  checked MD5 sums install ISO file, al matched. I used Ubuntu 16.x before with no problem.

---

### Post by oldfred on 2018-08-24
When you say pre-installed, you installed yourself, not from vendor.
So is Windows in UEFI or BIOS boot mode.

Post these:
sudo parted -l
sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb

With nVidia card you will need nomodeset.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Pein1911 on 2018-08-24
Yes i installed windows 10, and im sure it boot with UEFI, i dont use bios boot for very long time ago. I tried nomodeset when boot to install but still got same error. I tried in my laptop lenovo y500 too, i can go next step without proplem

---

### Post by oldfred on 2018-08-24
Does live installer work in live mode?
Can you use gparted to see drive?
Can you post the terminal output requested above on partitions?

What was on drive before, anything?

---

