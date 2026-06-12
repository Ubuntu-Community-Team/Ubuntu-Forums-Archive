---
title: "installing ubuntu 14.04 or higher on SSD with windows pre-installed"
date: 2015-12-19
forum: Installation &amp; Upgrades
---

### Post by Namana on 2015-12-19
Hi all,

I just recently bought [this]("http://www.amazon.com/G752VT-DH72-Gaming-Discrete-GeForce-Titanium/dp/B01578ZN0Q/ref=sr_1_11?s=pc&ie=UTF8&qid=1450573523&sr=1-11&keywords=asus+laptops&refinements=p_n_feature_four_browse-bin%3A2289792011%2Cp_n_feature_five_browse-bin%3A7817225011") laptop with Windows 10 pre-installed in it on the SSD. I want to install Ubuntu 14.04 on this SSD (does not matter if I had to remove Windows) and use 1 TB HDD to store data. The problem I am having is that Ubuntu installer does not detect SSD, it only shows 1 TB HDD. I have tried different versions of Ubuntu (14.04, 15.04, 15.10) but the same problem is there. Also, GParted is not able to show the SSD but windows shows both SSD and HDD. SSD had NVMe controller type and PCIe as controller interface whereas HDD has AHCI controller type and SATA as controller interface and the SATA Configuration is RAID. I am not able to figure out why the SSD is not being shown on Ubuntu installer or GParted. Does anyone have any idea what can be the reason?

Thanks in advance.
Naman Kumar

---

### Post by oldfred on 2015-12-19
I did see that gparted must be very new.
       gparted should be at least version 0.24.0-1 to recognize NVME devices

I thought I had the newest gparted, but it is from Sept and .23.
I am sure version in Ubuntu download is not as current as from gparted directly.
[http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.24.0-2/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.24.0-2/)

---

### Post by Namana on 2015-12-20
Yeah..I am using gparted 0.24.0-2 using a usb and it does not show SSD partition. Also, Ubuntu installer is not able to show SSD partition, it only shows HDD whereas windows shows both..
[COLOR=#111111][FONT=Ubuntu]It looks like it might be because Intel Rapid Storage Technology (RST) is enabled. Can this be the reason that GParted and Ubuntu is not able to see the SSD? There is no option to disable it from the UEFI. How can I disable it from Windows 10? [/FONT][/COLOR]Also, only windows can see SSD and it has OS installed on it.. Is it possible that it is locked so that no one else can see it? [COLOR=#111111][FONT=Ubuntu]Any help will be appreciated[/FONT][/COLOR]

---

### Post by oldfred on 2015-12-20
In UEFI you should be able to turn off Intel RST. And change to AHCI. But I believe the NVMe replaces AHCI. Also RAID should be off. Ubuntu desktop in newest versions recognizes RAID but may not install grub correctly, yet. You used to have to use the Alternative installer or the sever installer to use RAID or LVM. But with 12.04 they discontinued the alternative desktop installer. But did not immediately add LVM and RAID to desktop. Only recent versions do support LVM and seem to partially support RAID now.

 Fast Start up off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Older posts on RST, but will not help on the NVMe issues.

 [http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

### Post by Namana on 2015-12-20
Yeah...I am not able to find an option to turn off Intel RST in UEFI and switch to AHCI.. I dont think my laptop has that option (maybe, I am wrong). It just shows 1 TB HDD and 128 GB SSD in Intel RST in UEFI but no option to disable Intel RST in UEFI. Any suggestions regarding it will be appreciated. Also, Fast startup is off, secure boot is disabled. What do you mean when you say RAID should be off? SATA Controller is RAID but there is no option to change it or switch it off. Also, when I do sudo dmraid -E -r /dev/sda in **try ubuntu before installing**, I get "no raid disks and with names: "/dev/sda". 
Thanks!!

---

### Post by oldfred on 2015-12-20
Acer's now require a password to enable additional settings. Have not seen Asus with that requirement.
Most UEFI do have settings somewhere for Intel SRT. And from Linux the Intel SRT is seen as RAID, but it normally is not a standard RAID.

My Asus motherboard (Z97) has Intel SRT settings under PCH, somewhere in Advanced tab, but I have never even looked at those settings.

---

