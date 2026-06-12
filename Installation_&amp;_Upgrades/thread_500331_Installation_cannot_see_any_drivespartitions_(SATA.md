---
title: "Installation cannot see any drives/partitions (SATA1 drives)"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by CrossGAT on 2007-07-13
During the install from the LiveCD (v7.04) Ubuntu cannot see any drives/partitions on my two Sata1 drives, so I'm unable to proceed with the installation. Even the Linux file system formatted ones - ext3 & swap partitions - are not visible. The 'Prepare partition' applet in the install wizard has no drives/partitions listed - [screenshot](http://img527.imageshack.us/img527/4122/ubuntuinstallkz4.jpg).

Prior to this, when booting-up off the CD I get the following errors, then some lines of text like various things are loading & soon after the screen goes blank (& I have to reset the PC), or it boots into Ubuntu soon after:
[  189.250180 ata2.00: failed to set xfermode (err_mask=0x40)
[  224.709181 ata2.00: failed to set xfermode (err_mask=0x40)
[  260.168234 ata2.00: failed to set xfermode (err_mask=0x40)

Running in a terminal: 
*  sudo fdisk -l - gives nothing (it just returns to the command prompt: ubuntu@ubuntu:~$) 
*  sudo fdisk /dev/sda (or sdb) - gives 'unable to open /dev/sda'
*  sudo mount /dev/sda (or sdb) - gives 'can't find /dev/sda....'

Similar problem [_here_](http://ubuntuforums.org/showthread.php?t=388846) & [_here_](http://ubuntuforums.org/showthread.php?t=5472) but different motherboards. 

I like the look of Ubuntu & would like to have it dual-boot with XP. Any help appreciated. G

My system spec: 
- AMD 2800+ (32-bit)
- [_Gigabyte GA-7N400 Pro2_](http://www.giga-byte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=1678&ProductName=GA-7N400%20Pro2) - with nForce2 chipset & Silicon Image SATA controller
- ATi Radeon X800XT PE 256Mb (previously ATi 9700) 
- 80Gb (x2) Maxtor 6Y080M0 Sata1
- 1.5Gb PC3200  
- Pioneer DVR-111L

P.S. Incidentally, I had the same problem with Kubuntu (6.10) some months ago, so I downloaded the free version of Mandriva 2007 & managed to setup up a successful dualboot with XP Pro with the help of some guides on the web. It was the first time I had tried Linux. Amazingly, everything 'just worked' (including my ntl cable bb connection) - all with little/no input from me. All was fine for a while, until some months when I upgraded my graphics card I couldn't change the screen res beyond 640x480. After trying a few things, including starting from scratch & reinstalling Mandriva (couldn't manually install latest ATi drivers, btw), I still cannot change the res. So I though I'll move on & try something else.

---

### Post by CrossGAT on 2007-07-16
OK, I've given up on this & moved on to Freespire*. 

If someone posts a solution (or possibilities) it'll be useful to others who may encounter the same problem in the future. G

*Having some XP bootloader problems with it, but hope to sort it out with help from the Freespire boffins.

---

