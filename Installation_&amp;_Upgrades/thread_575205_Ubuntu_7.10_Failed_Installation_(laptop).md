---
title: "Ubuntu 7.10 Failed Installation (laptop)"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by lavinia on 2007-10-13
Hello all.
I downloaded and burned(12x)  desktop cd (ubuntu 7.10 rc.)
32 bit and 64 bit.

After reboot trying all options. but all function black screen. :mad: hdd stop... 

...

I am trying 64 bit cd. 
trying all options. but all function black screen. :mad: hdd stop... 
only 64 bit cd says(black screen) "kernel alive...."

 i go to BIOS settings.
change AHCI to Legacy Ide Mode

result: same(similar) problem.

I try to boot / install with the options noapic and lolapic by entering these in boot menu  But it is failed. 

My laptop info:

```
   Computer:
      Computer Type ACPI x86 computer  (Mobile)

    Motherboard:
      CPU Type :Mobile DualCore Intel Core 2 Duo T7300, 2000 MHz (10 x 200)
      Motherboard Name :Vestel Ares
      Motherboard Chipset :Intel Crestline GL960/GM965
      System Memory :2037 MB  (DDR2-667 DDR2 SDRAM)
      BIOS Type :Insyde (???????)

    Display:
      Video Adapter: Mobile Intel(R) 965 Express Chipset Family  (448 MB)
      Video Adapter :Mobile Intel(R) 965 Express Chipset Family  (448 MB)
      3D Accelerator: Intel GMA 3000
      Monitor: Samsung LTN154X3-L01  [15.4" LCD]

    Multimedia:
      Audio Adapter: Realtek ALC262 @ Intel 82801HBM ICH8M - High Definition Audio Controller

    Storage:
      IDE Controller: Intel(R) 82801HEM/HBM SATA AHCI Controller
      IDE Controller: Intel(R) ICH8M Ultra ATA Storage Controllers - 2850
      Storage Controller: Intel(R) Turbo Memory Controller
      Storage Controller: Microsoft iSCSI 
      Storage Controller: O2Micro Integrated MMC/SD controller
      Storage Controller: O2Micro Integrated MS/MSPRO Controller
      Disk Drive: FUJITSU MHW2160BH  (160 GB, 5400 RPM, SATA)
      Disk Drive: IMD-0  (512 MB, IDE)
      Optical Drive: TSSTcorp CD/DVDW SN-S082D ATA Device  (DVD+R9:6x, DVD-R9:4x, DVD+RW:8x/8x, DVD-RW:8x/6x, DVD-RAM:5x, DVD-ROM:8x, CD:24x/24x/24x DVD+RW/DVD-RW/DVD-RAM)
      SMART Hard Disks Status: OK

    Partitions:
      C: (NTFS) :84999 MB (56881 MB free)
      Total Size  :83.0 GB (55.5 GB free)

    Input:
      Keyboard: Standart 101/102 or Microsoft Natural PS/2 Klavye
      Mouse: HID ...
      Mouse: Synaptics PS/2 Port Pointing Device

    Network:
      Primary IP Address: 192.168.2.2
      Primary MAC Address: ...
      Network Adapter: Bluetooth ...
      Network Adapter: Intel(R) 82566MC Gigabit Platform LAN Connect
      Network Adapter :Intel(R) Wireless WiFi Link 4965AGN  (192.168.2.2)
      Modem: Motorola SM56 Data Fax Modem

    Peripherals:
      Printer: Microsoft XPS Document Writer
      FireWire Controller: O2Micro OHCI Compliant IEEE1394 Host Controller
      USB1 Controller :Intel 82801HBM ICH8M - USB Universal Host Controller
      USB1 Controller  :Intel 82801HBM ICH8M - USB Universal Host Controller
      USB1 Controller:  Intel 82801HBM ICH8M - USB Universal Host Controller
      USB1 Controller: Intel 82801HBM ICH8M - USB Universal Host Controller
      USB1 Controller: Intel 82801HBM ICH8M - USB Universal Host Controller
      USB2 Controller: Intel 82801HBM ICH8M - USB2 Enhanced Host Controller
      USB2 Controller: Intel 82801HBM ICH8M - USB2 Enhanced Host Controller
      USB Device: Generic Bluetooth Radio
      USB Device: USB ...
      USB Device : USB2.0 1.3M WebCam
      Battery : Microsoft AC ...
      Battery   : Microsoft ACPI ...

    DMI:
      DMI BIOS Vendor: VESTEL
      DMI BIOS Version: ARES 0.18
      DMI System Manufacturer: VESTEL
      DMI System Product: ARES
      DMI System Version: 1
      DMI Motherboard Manufacturer :Intel Corp.
      DMI Motherboard Product : Base Board Product Name
      DMI Motherboard Version :Base Board Version
      DMI Motherboard Serial Number   :Base Board Serial Number
      DMI Chassis Manufacturer :Chassis Manufacturer
      DMI Chassis Version :Chassis Version
      DMI Chassis Serial Number  :Chassis Serial Number
      DMI Chassis Asset Tag :Chassis Asset Tag
      DMI Chassis Type   

--------[ Debug - PCI ]-------------------------------------------------------------------------------------------------

    B00 D00 F00:  Intel GL960/GM965/PM965 Chipset - Memory Controller Hub
                  
...

    B00 D02 F00:  Intel GL960/GM965 Chipset - Graphics Controller 0
                  
..

    B00 D02 F01:  Intel GL960/GM965 Chipset - Graphics Controller 1
                  
...

    B00 D19 F00:  Intel 82566MC Gigabit Network Controller
                  
...

    B00 D1A F00:  Intel 82801HBM ICH8M - USB Universal Host Controller
                  
...

    B00 D1A F01:  Intel 82801HBM ICH8M - USB Universal Host Controller
                  
..

    B00 D1A F07:  Intel 82801HBM ICH8M - USB2 Enhanced Host Controller
                  
...

    B00 D1B F00:  Intel 82801HBM ICH8M - High Definition Audio Controller
                  
 ..

    B00 D1C F00:  Intel 82801HBM ICH8M - PCI Express Root Port 1
                  
...

    B00 D1C F01:  Intel 82801HBM ICH8M - PCI Express Root Port 2
                  
 ..

    B00 D1C F02:  Intel 82801HBM ICH8M - PCI Express Root Port 3
                  
...

    B00 D1D F00:  Intel 82801HBM ICH8M - USB Universal Host Controller
                  
..

    B00 D1D F01:  Intel 82801HBM ICH8M - USB Universal Host Controller
..

    B00 D1D F02:  Intel 82801HBM ICH8M - USB Universal Host Controller
                  
..

    B00 D1D F07:  Intel 82801HBM ICH8M - USB2 Enhanced Host Controller
                  
..

    B00 D1E F00:  Intel 82801HBM I/O Controller Hub 8 (ICH8M)
                  
...
    B00 D1F F00:  Intel 82801HBM ICH8M-DO - LPC Bridge
                  
...

    B00 D1F F01:  Intel 82801HBM ICH8M - PATA Controller
                  
...

    B00 D1F F02:  Intel 82801HBM ICH8M - SATA AHCI Controller
                  
..

    B00 D1F F03:  Intel 82801HBM ICH8M - SMBus Controller
                  
...

    B01 D00 F00:  Intel 4965AGN PRO/Wireless Network Adapter
                  
...

    B03 D00 F00:  Intel Flash Response Memory Technology (Robson)
                  
.
...

    B04 D02 F00:  O2Micro OHCI Compliant IEEE1394 Host Controller
                  
...

    B04 D02 F02:  O2Micro Integrated MMC/SD Controller
                  
...
    B04 D02 F03:  O2Micro Integrated MS/xD/SM Controller
                  
...

    PCI-8086-2A00:  Intel i965M MCHBAR
                  
...

    PCI-8086-2A00:  Intel i965M MCHBAR
                  
....

    PCI-8086-2A00:  Intel i965M MCHBAR
                  
...


--------[ Debug - Video BIOS ]------------------------------------------------------------------------------------------

....


--------[ Debug - Unknown ]---------------------------------------------------------------------------------------------

    FW PHY          Unknown (00000CC2-00401104)
    HDD             IMD-0


```

SORRY FOR  deficient language. :(

Please help me. I love you linux i love you ubuntu :sad:

---

### Post by lavinia on 2007-10-14
Please...
:(

---

### Post by vanillalisterine on 2007-10-14
i'm having the same problem as lavinia with my 965 express chipset.

changed bios boot order and slipped in a 7.04 32-bit pc cd.  waited about five minutes on a black screen with a blinking cursor key and then was greeted by a vista bootup.

tried a 6.06 32-bit pc cd next.  worked fine...until it came to loading x--which failed completely.  got an odd error message (i'll upload it if anyone wants to see).

soo i tried 5.10 next.  was fine until i came to partitioning.  i'm not familiar with partitioning...but i tried all of the options and in the end, partioning failed.  got different sorts of error messages.  ug.

help pleaseeee.  i'm fed up with vista and i've used it for only two days.

---

### Post by dolo724 on 2007-10-15
vanillalisterine, 
 if you use the alternate install CD you might have success installing, then use "sudo apt-get install [k,x]ubuntu-desktop" to get a different desktop manager if you need it.

Beware, you might have interesting video issues on an otherwise workable system. See some of the installation and video solutions here: [http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

---

### Post by jjcv on 2007-10-15
Sounds like a problem with the video card.

Try a ctr-alt-backspace to see if you can get to a console.   Alt-F1, Alt-F2 .... allow to switch to virtual screens.

Check you video card with dmesg.

---

### Post by lavinia on 2007-10-15
Thanks for replys messages...

dolo724; I downloaded alternate cd. Select text mode install..
But same problem :confused:

(my hardware infos: above)

---

### Post by dolo724 on 2007-10-15
Lavinia, 
 try the 32-bit 7.04 alternate CD. I had the same problem with my machine with the Intel 965 graphics. 

Also, the forum I listed above has some good procedures, even if it is for another type of computer. 
Keep notes on what you try, then post it here whether it works or not.

---

### Post by lavinia on 2007-10-15
dolo724 thanks for reply.

Dolo724; Already i have 32 bit alternate 7.04 cd ...

i select and enter "text mode install" but wait 30-40 minutes..
result: black screen, blinking cursor...

---

### Post by lavinia on 2007-10-16
I downloaded pclinuxos 2007.

select and enter safe install.. ok installing and works.. :shock:

---

### Post by hamishau on 2007-10-16
This may have nothing to do with it, but I need to put "hpet=disable" at the end of the kernel boot line (see below):

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6cfb9591-e3bd-444f-9d10-108d13efaf7a ro quiet splash hpet=disable
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

When I installed I made that change and it kept it with the install. Alternatively you can edit the /boot/grub/menu.lst file to add it in.

As I said, this works for me, so I hope this helps for you too

Haish

---

### Post by PmDematagoda on 2007-10-16
You burnt the CD too quick lavinia, X12 is too fast as it can corrupt the CD, burn it at 4X and try again.

---

### Post by lavinia on 2007-10-16
Thanks for reply hamishau, PmDematagoda.
 hamishau; ok trying this today.

PmDematagoda cd check and other test: no  problem. 
And i installed my desktop pc: no problem:

and installation test pclinuxos 2007: no problem.

Problem only on ubuntu 7.10, 7.0.4


:(

---

### Post by jimbo99 on 2007-10-16
I have about 5 laptops that are quality enough (or better) to turn ubuntu but no matter how  hard I try I can't get it to install without potential serious issues.  Most are compaq or HP laptops.  Two are toshiba but I've tried on only one and it works but I can't get the video to work properly nor the accelerated drivers to work.  Under XP the accelerated drivers work fine.

I haven't tried any other distros and just thought that it might be a good decision to try them out.

---

### Post by lavinia on 2007-10-17
My laptop x86 acpi computer mobile.

I solved my problem. But disable acpi apic...
Ubuntu does not supporting acpi and apic :(

---

### Post by kingofbananas on 2008-01-16
Sorry for bumping an old topic, but i have exactly the same problem and also a vestel mainboard.

noapic nolapic did not help me and also hpet=disable did not help.. i disabled quiet to see where it locks up and it seems that it happens at:
(without hpet=disable) Total of 1 processors found.
(with hpet=disable) a little bit further and it also finds the 2nd processor.

I don't have access to my laptop right now so I can't post the system specs, but I also tried installing fedora which resulted in the same lock up..

I verified that the cd is burned correctly and everything is ok...
(I tried alternate and normal version)

edit: I found the solution: [http://ubuntuforums.org/showthread.php?t=641354](http://ubuntuforums.org/showthread.php?t=641354) ...
disabling legacy support for usb drives did the trick

---

