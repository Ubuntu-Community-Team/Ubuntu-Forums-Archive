---
title: "Having an issue booting into Xubuntu 14.04 after Grub installation error."
date: 2014-08-15
forum: Installation &amp; Upgrades
---

### Post by Sina_Amini on 2014-08-15
When going through the installation process I chose the option to install Xubuntu along side Windows 8.1 and I let the installer take care of the partitions. The reason for that was because the tutorials I had seen involving doing the partitions manually didn't have existing partitions like my hard drive had.

So looking at my hard drives now I can see that Xubuntu is clearly installed but I can seem to boot into it. I want to fix this some how but I'm not sure what the best option would be. I tried using Rescatux on a live CD but that didn't work. 

----

I'm running Windows 8.1 on a Lenovo Y500 using an i7.

I'm using a Sandisk Cruzer 8GB flash drive with "xubuntu-14.04.1-desktop-i386.iso" installed on to it. I use that to boot into istallation.

In order for me to be able to boot into a USB I had to change my BIOS settings to Legacy and turn off Fast Boot as well as Secure Boot.

----

For some more information here are some screen caps of my hard drive partitions. 

[http://i.imgur.com/Yn9R6Oq.jpg](http://i.imgur.com/Yn9R6Oq.jpg)

[http://i.imgur.com/fva6RPL.jpg](http://i.imgur.com/fva6RPL.jpg)


*[SIZE=3]If you need any more information that could help please let me know and I will do my best to provide it.  [/SIZE]*

---

### Post by grahammechanical on 2014-08-15
Did you follow this guide?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]

> 
[COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[/FONT]
[/LIST]


You should not be using i386 but amd64. Does Windows still boot?

Regards.

---

### Post by Sina_Amini on 2014-08-15
I didn't use that guide but I will check it out now. The only reason why I had to switch to legacy is because windows 8 wouldn't let me boot from a usb to install xubuntu. 

I will try to install the amd64 version and see what happens. I'm not sure if ill be able to boot from usb if I switch back to UEFI mode though.

---

### Post by oldfred on 2014-08-15
Stop. Do not run any auto reinstall option. That will overwrite entire drive.

       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

The only safe reinstall is Something Else where you manually select a partition, its new format, its mount like / (root) or reuse previous root. It will auto find swap. If /home was a separate partition you must select it but DO NOT select format.

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by Sina_Amini on 2014-08-16
I actually did auto reinstall last night and it didn't wipe everything. Although it still did give me that error with grub. So I'm putting the amd54 iso on a flash drive now. I also switched back to UEFI mode but I dont think my pc will let me boot from usb now. That was the reason I had to switch to legacy. 

I'm going to have to find a way to get rid of the previous xubuntu install and retrieve all the partitioned hard drive space. 

Will report back with results once I reboot.

---

### Post by Sina_Amini on 2014-08-16
Windows is still booting. I just tried to boot from my usb that now has the amd64 version on it but it's not letting me boot from usb anymore now that I'm in UEFI mode. The boot from usb option only comes up when I'm in legacy mode. Secure boot and fast boot are both off as well. I'm not sure what the problem is exactly.

---

### Post by oldfred on 2014-08-16
Post link from report with Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
UEFI is often similar across models. Just different for different options. AMD & Intel are where there are major differences. Other Lenovo

 Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)
Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)
Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

---

