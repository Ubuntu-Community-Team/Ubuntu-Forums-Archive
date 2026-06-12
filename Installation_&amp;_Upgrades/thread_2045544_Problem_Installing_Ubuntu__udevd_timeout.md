---
title: "Problem Installing Ubuntu : udevd timeout"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by soumyasd on 2012-08-21
Hi, 

I've trying to install Ubuntu on a machine with the following configuration. 




[LIST]
[*]Dell PrecisionT 5600n, 635W
[*]Processor Dual Six Core XEON E5-2630, 2.2GHz,  15M, 7.2 GT/s,Turbo
[*]Memory 64GB, DDR3 RDIMM Memory,  1600MHz, ECC (8 x 8GB DIMMs)
[*]Graphics 1.0GB NVIDIA® Quadro® 600, Dual  MON, 1 DP & 1 DVI
[*]Boot Hard Drive 256GB, 2.5" SATA 6Gb/s Solid State Drive
[*]Hard Drive Configuration C2 SATA/SSD 2.5 Inch, 1-2 Hard Drives
[*]PERC Controller PERC H310 SATA/SAS Controller for  Dell Precision
[*]DVD and Read- Write Devices 8X DVD+/-RW SATA, Data Only
[*]Power Supplies 635W Power Supply, 85% Efficiency
[*]Intel Chipset  Controller Integrated Intel chipset controller
[*]Systems Management No Out-of-Band Systems Management
[*]Hard Drive RAID No RAID
[*]Multi select Monitors
[*]Dell Professional P2312H, Wide 
[*]screen,23in VIS,HAS,VGA,DVI
[/LIST]


Everytime the install stops at [FONT="Courier New"]usbhid: USB HID core driver[/FONT] and after I while I see the following error messages

[FONT="Courier New"]
udevd[223]: timeout: killing '/sbin/modprobe -bv pci:v00001000d00000073sv00001028sd0000iF78bc01sc04i00' [337][/FONT]

 on the screen. I've attached two screen shots that show these errors. 

**I've tried both Ubuntu Desktop 12.04 and Ubuntu Server 12.04. I've also tried Kubuntu 12.04 LTS. I also tried a Ubuntu 11.04 but with similar results. **

I've tried the following boot options and none of them work. 

1. Adding nomodeset 
2. nolapic
3. noapic
4. removing splash 

I even changed the hard drive from the solid state drive to a normal Segate 500GB disk drive. It didn't make any difference. 
I got the same error. 

I then tried to boot the system without any hard drive and I still got the same error. 

I tried installing Windows 7 64-bit and it couldn't detect any drives. 

Any idea what's going on ? Do I've a hardware issue or a drive issue ? 

Any help will be greatly appreciated. 

thanks.

---

### Post by dino99 on 2012-08-21
There is so much issues with Dell config that a special subforum has been created; better to search & ask there.

---

### Post by Schpammor on 2012-09-05
@dino99: so i seem to have a similar problem. because of the mentioned dell subforum i posted it there instead of replying here, so check [http://ubuntuforums.org/showthread.php?p=12218877](http://ubuntuforums.org/showthread.php?p=12218877) maybe.
in your case the modprobe seems to fail for "IBM ServeRAID M1015" (chip described by the vendor and device id of the error message).
[]("http://ubuntuforums.org/showthread.php?p=12218877")

---

