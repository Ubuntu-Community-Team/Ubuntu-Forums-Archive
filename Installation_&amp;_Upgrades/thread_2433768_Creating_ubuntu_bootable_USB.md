---
title: "Creating ubuntu bootable USB"
date: 2019-12-25
forum: Installation &amp; Upgrades
---

### Post by Dedalo on 2019-12-25
Hi. I'm about to build a new machine, and I'll be installing ubuntu on it. I have bought all the parts of this pc, and I have to build it from zero. I have never done this before. However, I have installed ubuntu on many systems, many times. All those times, I have created an ubuntu bootable usb from windows. I would like to know if it is possible to create the bootable usb from ubuntu itself, so I don't have to use a windows system in the process. Any other advices to start this system for the very first time will be also welcome.

The specs of this system are (in case you have any recommendations on the building itself):

Motherboard: ASRock Fatal1ty B450 Gaming K4.
CPU: Ryzen 7 2700.
GPU: GTX 1060, 3GB.
RAM: G.skill Tridentz Rgb 16gb (2 X 8gb) 3200 Mhz- For Amd (G.SKILL F4-3200C16D-16GTZRX).
SSD: Ssd Wd 240gb Green M.2 Western Digital.
Power supply: Evga Bronze 600w 80 Plus 49amp.
Chassis: Thermaltake V100 Black Mid Tower 1.

---

### Post by oldfred on 2019-12-25
Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or  

 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Since new UEFI based system, you will want gpt partitioning & UEFI install.
And since nVidia, you will need nomodeset boot parameter to boot installer and first boot or until you install nVidia proprietary driver. Very newest Ubuntu may now offer to install nVidia driver during install.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[URL="https://help.ubuntu.com/community/Grub2"]https://help.ubuntu.com/community/Grub2

      [/URL]Asrock B450M Steel Legend - turn UEFI Secure Boot off
[URL="https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine"]https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine
      [/URL]
  Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679) 
    [URL="https://help.ubuntu.com/community/Grub2"]
[/URL]Issues are mostly by vendor, but some are by model. Not sure if any of this may apply.
      
 Gigabyte B450 Ryzen needs kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247) & 
[https://ubuntuforums.org/showthread.php?t=2423649](https://ubuntuforums.org/showthread.php?t=2423649)

---

### Post by Dennis N on 2019-12-25
> Fatal1ty B450 Gaming K4
Wow. That's a scary name for a motherboard. Other advice: plan your assembly steps ahead and proceed slowly. Be sure ram modules are fully plugged in. Watch status leds on the board on first boot for indications of problems.

Oh...and get yourself a magnetized screwdriver if you don't have one.

---

### Post by Dedalo on 2019-12-25
Great, thanks a lot!

BTW, the gpu isn't new, I bought it used. I haven't gone for it yet, but I don't think I'll have the drivers (I haven't bought any cd reading device anyway). Can I install the drivers for it online, after installing the OS?

---

### Post by bunny9000 on 2019-12-25
I've always used unetbootin on windows and Linux for all Linux distros over EFI and legacy. Your mileage may vary.

P.S. Get the samsung SSD either m2 or 2.5in in the evo line - still the best SSD line on the market.

Thank me later. \\:D/

P.P.S - You might want to consider the corsair CX lineup of power supplies. 

Slightly jealous of the ryzen though. Really want to get my hands on some of the newer amd stuff.

---

### Post by oldfred on 2019-12-25
The nVidia drivers are in the Ubuntu repository, but then each version of Ubuntu may have older versions. For newest available version there is  a ppa that you add and then repository is updated with all the latest drivers.

        [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade 
   sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
   # If later you do not want ppa, how to uninstall ppa
sudo add-apt-repository --remove ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by Dedalo on 2019-12-25
nvidia-XXX, I like that version :lolflag:

Thanks a lot Fred! I'll be back if something goes wrong. Wish me luck. I'll probably do it during the weekend.

---

### Post by Dedalo on 2019-12-29
> **oldfred said:**
> Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or  


Hi Fred. Yesterday I built the new pc. I booted it for the first time, and entered the BIOS. Then I prepared an usb stick to install ubuntu. However, in the installation wizard my m.2 ssd haven't appeared, so I wasn't able to finally install it. Any idea of what could be going on? I think the m.2 is properly installed, it has only one position, and it is fixed with a screw.

---

### Post by oldfred on 2019-12-29
Almost all new systems seem to still need UEFI & SSD firmware update.
Often easier from Windows, but now a few systems can be updated directly from Linux. But have yet to see any motherboard manufacturers on list.

My UEFI can update directly from UEFI, if the downloaded update file is in a FAT32 formatted partition. I change permissions on my ESP, and use that. You can use a FAT32 formatted flash drive.
SSD vendors often have their own software.  Other ways are from Windows & from a DOS formatted bootable flash drive to run the .exe, but you still have update file separate.

Samsung used to hide the Linux update version under commercial updates, not consumer. Not sure now. Other vendors you will have to search.

---

### Post by Dedalo on 2019-12-29
So I need to update the BIOS for my MOBO?

---

### Post by Dedalo on 2019-12-29
> **oldfred said:**
> Almost all new systems seem to still need UEFI & SSD firmware update.
Often easier from Windows, but now a few systems can be updated directly from Linux. But have yet to see any motherboard manufacturers on list.

My UEFI can update directly from UEFI, if the downloaded update file is in a FAT32 formatted partition. I change permissions on my ESP, and use that. You can use a FAT32 formatted flash drive.
SSD vendors often have their own software.  Other ways are from Windows & from a DOS formatted bootable flash drive to run the .exe, but you still have update file separate.

Samsung used to hide the Linux update version under commercial updates, not consumer. Not sure now. Other vendors you will have to search.

I've updated the BIOS to one of the newer versions (P3.40 from [https://www.asrock.com/mb/AMD/Fatal1ty%20B450%20Gaming%20K4/index.es.asp#BIOS](https://www.asrock.com/mb/AMD/Fatal1ty%20B450%20Gaming%20K4/index.es.asp#BIOS) ). But the issue wasn't solved.

This is the screen I get, as can be seen, the only storage device available is the USB drive:

[IMG]https://i.ibb.co/NVX8r19/20191229-154851.jpg[/IMG]

---

### Post by oldfred on 2019-12-29
Are drives set to AHCI in UEFI?

---

### Post by Dedalo on 2019-12-30
> **oldfred said:**
> Are drives set to AHCI in UEFI?

Hi. How can I check that? 

however, I fixed it, someone in reddit told me how to fix it. I had installed my m.2 in the wrong slot, it turns out that my m.2 is sata, and I've used the m.2 NVMe slot. Now it works.

Thanks.

---

