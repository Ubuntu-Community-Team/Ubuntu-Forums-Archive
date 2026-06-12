---
title: "I can not install Ubuntu on my Dell Inspiron 7559"
date: 2016-07-24
forum: Installation &amp; Upgrades
---

### Post by giuliopaparelli on 2016-07-24
Hi everyone. I just bought a new laptop, the Dell Inspiron 7559 (I7 6700HQ, NVidia 960M), which is certified with Ubuntu 14.04 LTS, but I can't install it. To be more specific, I really can't install Linux, I have problems with other distros too (I'd like to install Kali Rolling, but it freeze after login).
Anyway, the problem with Ubuntu is even worse, when I boot the USB the installation freeze immediately on the load (with the "4 points"). It happens with Ubuntu 14.04 LTS (64bit), XUbuntu 14.04 LTS and Ubuntu 16.04 LTS. 
I use Rufus for burn the ISO, the correct burn way is GPT for UEFI, and I can burn this way just Ubuntu 16.04. For the other version I use Win32 for create bootable drives.

I really need a Linux distro on my laptop, please help me, thank you a lot.

---

### Post by mook765 on 2016-07-24
Rufus doesn't support 16.04 version off ubuntu, i tried a lot off aother similar tools as well with the same effect.
make sure to check md5 or sha256 checksums off your downloaded iso and burn a dvd at lowest speed wich is supported by your dvd-drive.
if your laptop doesn't have a DVD-drive, use external USB-DVD-drive, if you dont have one, maybe you can borrow one from friends.
after you boot from dvd, choose to check filesystem integrity first.when you see the splashscreen, you can press Esc to see the messeges produced by the check. iff there is any error, just burn a new dvd...
good luck

---

### Post by oldfred on 2016-07-24
You can just make your own UEFI only bootable flash drive:
 Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

With nVidia you may need nomodeset for both live installer and your install until you install proprietary driver from Ubuntu repository.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 10 screens or similar to Windows 8
[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi

      [/URL]
 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
    [URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]
[/URL]

---

