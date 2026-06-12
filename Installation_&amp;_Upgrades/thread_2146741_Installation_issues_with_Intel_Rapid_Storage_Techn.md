---
title: "Installation issues with Intel Rapid Storage Technology"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by KKuff on 2013-05-19
Hi,
I am trying to install Ubuntu 13.04 to dual boot with Windows 8 (not factory installed) on my Lenovo u310 laptop. The laptop has a 32GB SSD cache that uses Intel's Rapid Storage Technology in addition to a 500GB HDD. At first, the installer was unable to see the HDD, and after a little bit of research, I found that running the command ```
sudo dmraid -E -r /dev/sdb
``` fixed the issue of the HDD being seen by the installer, so I ran the installer, and installation completed. After restarting, I now get a Intel Rapid Storage Technology display that lists RAID volumes and Physical devices, along with a prompt to press CTRL +I to enter configuration utility. The RAID volumes and physical devices listed are as follows:
RAID Volumes:
 [TABLE="width: 500"]
[TR]
[TD="width: 25"]             ID[/TD]
[TD="width: 67"]             Name[/TD]
[TD="width: 116"]             Level[/TD]
[TD="width: 58"]             Strip[/TD]
[TD="width: 62"]             Size[/TD]
[TD="width: 70"]             Status[/TD]
[TD="width: 74"]             Bootable[/TD]
[/TR]
[TR]
[TD="width: 25"]             0[/TD]
[TD="width: 67"]             FFS[/TD]
[TD="width: 116"]             RAID0(Stripe)[/TD]
[TD="width: 58"]             128KB[/TD]
[TD="width: 62"]             8.0GB[/TD]
[TD="width: 70"]             Normal[/TD]
[TD="width: 74"]             Yes[/TD]
[/TR]
[TR]
[TD="width: 25"]             1[/TD]
[TD="width: 67"]             CACHE[/TD]
[TD="width: 116"]             RAID0(Cache)[/TD]
[TD="width: 58"]             128KB[/TD]
[TD="width: 62"]             21.8GB[/TD]
[TD="width: 70"]             Disabled[/TD]
[TD="width: 74"]             No[/TD]
[/TR]
[/TABLE]
 Physical Devices:
 [TABLE="width: 500"]
[TR]
[TD="width: 21"]             ID[/TD]
[TD="width: 148"]             Device Model[/TD]
[TD="width: 131"]             Serial #[/TD]
[TD="width: 62"]             Size[/TD]
[TD="width: 119"]             Type/Status(Vol ID)[/TD]
[/TR]
[TR]
[TD="width: 21"]             0[/TD]
[TD="width: 148"]             SAMSUNG MZMPC032[/TD]
[TD="width: 131"]             S0Y2NEAC643027[/TD]
[TD="width: 62"]             29.8GB[/TD]
[TD="width: 119"]             Cache Disk(0,1)[/TD]
[/TR]
[TR]
[TD="width: 21"]             1[/TD]
[TD="width: 148"]             ST500LT012-9WS14[/TD]
[TD="width: 131"]             W0V0Q2Z4[/TD]
[TD="width: 62"]             465.7GB[/TD]
[TD="width: 119"]             Non-RAID Disk[/TD]
[/TR]
[/TABLE]
 
If I don't press CTRL+I, booting fails, and I am brought to a screen to select boot device, and this list contains:
1. RAID DEVICE2: ST500LT012-9WS14
2. RAID DEVICE1: INTEL FFS
3. PCI LAN:  Realtek PXE B02 D00

I've tried the first two options, although I believe that the first one should be the correct option.  Neither one works, I am just brought back to this menu after it attempts to boot.

I tried using Boot-Repair, but after restarting, I still get the same results as before.  Here is the configuration detected by Boot-Repair before I ran it:  [http://paste.ubuntu.com/5680351/](http://paste.ubuntu.com/5680351/) .  This is after I ran it:  [http://paste.ubuntu.com/5680386/](http://paste.ubuntu.com/5680386/).

I think what happened is that when I ran the dmraid -E -r command, that I erased the RAID data needed for IRST.  I would appreciate any help in order to get this working.  I don't mind completely reinstalling Windows and Ubuntu from scratch if I have to.

Thanks

---

### Post by KKuff on 2013-05-20
So I was able to get it working without reinstalling Windows.  I went into BIOS and disabled UFEI, changed the SATA controller from RAID to ACHI, and disabled Intel Rapid Storage Technology.  Then I booted from the Ubuntu live usb and used fdisk to remove the partitions that I created to install Ubuntu.  I ran the dmraid -E -r command on both drives, then reinstalled Ubuntu, this time choosing the "Alongside other operating system" option instead of "Something else".  Ubuntu installed successfully, and I was able to boot into Ubuntu or Windows 8.  But now, Windows 8 would just go into "Auto Repair".  I went into BIOS and changed all of the previous settings back, except for UFEI.  Then I tried to boot Windows again, and did a system restore from the auto repair menu.  The system restore was succesful and I was able to boot into both Windows and Ubuntu.  After this, I went into IRST inside Windows, and reenabled acceleration using the SSD as a cache.  Everything seems to be working fine now.

Also, there is some useful information here:  [http://ubuntuforums.org/showthread.php?t=2129157&page=2](http://ubuntuforums.org/showthread.php?t=2129157&page=2) , that I wish I found before I started doing this.

---

### Post by riccardosl45 on 2014-02-20
> **KKuff said:**
> So I was able to get it working without reinstalling Windows.  I went into BIOS and disabled UFEI, changed the SATA controller from RAID to ACHI, and disabled Intel Rapid Storage Technology.  Then I booted from the Ubuntu live usb and used fdisk to remove the partitions that I created to install Ubuntu.  I ran the dmraid -E -r command on both drives, then reinstalled Ubuntu, this time choosing the "Alongside other operating system" option instead of "Something else".  Ubuntu installed successfully, and I was able to boot into Ubuntu or Windows 8.  But now, Windows 8 would just go into "Auto Repair".  I went into BIOS and changed all of the previous settings back, except for UFEI.  Then I tried to boot Windows again, and did a system restore from the auto repair menu.  The system restore was succesful and I was able to boot into both Windows and Ubuntu.  After this, I went into IRST inside Windows, and reenabled acceleration using the SSD as a cache.  Everything seems to be working fine now.

Also, there is some useful information here:  [http://ubuntuforums.org/showthread.php?t=2129157&page=2](http://ubuntuforums.org/showthread.php?t=2129157&page=2) , that I wish I found before I started doing this.

is your Ubunutu installation running on a separate partition with ext4?

---

