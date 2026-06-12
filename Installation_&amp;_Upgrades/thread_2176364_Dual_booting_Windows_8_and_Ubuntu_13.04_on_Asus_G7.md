---
title: "Dual booting Windows 8 and Ubuntu 13.04 on Asus G750JX"
date: 2013-09-24
forum: Installation &amp; Upgrades
---

### Post by demonicpagan on 2013-09-24
I don't know where I am going wrong here as I have done everything proper from what I have read, but I cannot get into a Live session from either my USB or CD. The following things are set in my BIOS:

Vendor: American Megatrends
Version: 208
[LIST]
[*]Fast Boot: Disabled
[*]Launch CSM: Disabled
[*]Secure Boot: Disabled
[/LIST]

I boot my Live(USB/CD) under UEFI mode and select "Try Ubuntu without installing" and all I get is a black screen. I am not able to progress any further. I have also turned off Fast Startup through Widows 8.

What my goal is to install Ubuntu on my partitioned terabyte HDD (Storge partition of 766.51 GB and 165 GB partition for Ubuntu, both are GPT). Windows 8 will stay on my other HDD in which it was installed.

I appreciate any help I can get to install Ubuntu on my machine under UEFI.

---

### Post by oldfred on 2013-09-24
What video card/chip do you have?
Have you tried nomodeset?

If installing to a second drive make sure it is gpt partitioned. I might also have an efi partition at the beginning of drive even if actually using the other drive's efi as default. Then you can also make drive independently bootable with its own boot files.

See alslo links in the link in my signature.

---

### Post by demonicpagan on 2013-09-24
I have an Nvidia Geforce GTX 770M. I did try editing the "Try Ubuntu without installing" command to read the following:

> 
setparams 'Try Ubuntu without installing'

     set gfxpayload=keep
     linux /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper nomodeset --
     initrd /casper/initrd.lz

---

### Post by oldfred on 2013-09-24
Usually you do not edit to add nomodeset boot line on flash drive, but that should work. You can just edit as you boot on grub menu with UEFI or f6 on BIOS boot.

---

### Post by demonicpagan on 2013-09-24
I don't get any option to hit f6 on BIOS boot. Upon booting from my Live(CD/USB) I see this:

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

Not this:

[IMG]http://sdnalloh.com/wp-content/uploads/2012/07/Ubuntu-12.04-nomodeset.png[/IMG]

---

### Post by oldfred on 2013-09-24
To get to that screen with f6, you have to press the infamous 'any' key when the tiny accessibility (keyboard & person) icons show at bottom of very first screen.
I think that is supposed to mean press a key on keyboard. But I have no idea why they would use icons when they could just show menu like they did years ago.

---

### Post by demonicpagan on 2013-09-24
> **oldfred said:**
> To get to that screen with f6, you have to press the infamous 'any' key when the tiny accessibility (keyboard & person) icons show at bottom of very first screen.
I think that is supposed to mean press a key on keyboard. But I have no idea why they would use icons when they could just show menu like they did years ago.

I don't even get that screen. It boots directly to the GRUB menu

---

### Post by oldfred on 2013-09-24
Then are you booting in UEFI mode not BIOS mode. At grub menu you should press e and scroll to linux line. Change quiet splash to nomodeset.
Your edit of BIOS syslinux boot does not change the grub boot in UEFI mode.

---

### Post by demonicpagan on 2013-09-24
> **oldfred said:**
> Then are you booting in UEFI mode not BIOS mode. At grub menu you should press e and scroll to linux line. Change quiet splash to nomodeset.
Your edit of BIOS syslinux boot does not change the grub boot in UEFI mode.

> **demonicpagan said:**
> I have an Nvidia Geforce GTX 770M. I did try editing the "Try Ubuntu without installing" command to read the following:
> 
setparams 'Try Ubuntu without installing'

set gfxpayload=keep
linux /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper nomodeset --
initrd /casper/initrd.lz


Upon reading [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) it says I should be booting in UEFI mode. The only way to boot into BIOS mode is by setting "Launch CSM" to Enabled. By doing that and installing Ubuntu 13.04 under the "Legacy" mode could do serious harm to my system and not be able to boot back into Windows 8. 

Upon hitting F10 after the edit of the entry under UEFI mode, I get a steady black screen and can't progress any further. Unless I am completely missing where I'm to be making this edit.

---

### Post by oldfred on 2013-09-24
That looks correct. 
Does this system have dual video? Or both Intel & nVidia? And can you set which is used from UEFI/BIOS?


While these were Toshiba's I think the settings were required more because they are Haswell.
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by demonicpagan on 2013-09-24
> **oldfred said:**
> That looks correct. 
Does this system have dual video? Or both Intel & nVidia? And can you set which is used from UEFI/BIOS?


While these were Toshiba's I think the settings were required more because they are Haswell.
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

This system does not have dual video, just nVidia.

---

### Post by oldfred on 2013-09-24
then try some of the other boot options that Haswell systems seemed to need. Not sure if just those or in addition to nomodeset.

Edit.
While we normally do not suggest the next version of Ubuntu until it is released except for testers, your hardware is so new that the very newest kernel and support software may really be required.
If you do install 13.10 understand is currently is about at beta, will have more changes. Each change may have issues and sometimes you may not even be able to boot. If issue is repeatable you should report as bug.

 How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)

---

### Post by demonicpagan on 2013-09-25
Here are some images from my BIOS:

Main:
[[IMG]http://i.imgur.com/sTQ4Rqel.jpg[/IMG]](http://imgur.com/sTQ4Rqe)

Advanced:
[[IMG]http://i.imgur.com/A2QGeuAl.jpg[/IMG]](http://imgur.com/sTQ4Rqe)

Boot:
[[IMG]http://i.imgur.com/j1U5TKll.jpg[/IMG]](http://imgur.com/j1U5TKl)

Security:
[[IMG]http://i.imgur.com/0HnWIpCl.jpg[/IMG]](http://imgur.com/0HnWIpC)

Secure Boot Menu:
[[IMG]http://i.imgur.com/YfTb7hfl.jpg[/IMG]](http://imgur.com/YfTb7hf)

I am downloading 13.10 and see if anything is different when I attempt to boot and install. I'll post my findings once I have done as such. This isn't my first beta rodeo, so I know things are bound to change. Part of me working on this is to assist a professor of mine work on how to potentially resolve issues such as this. An assignment he has has his students download Ubuntu and mess around with it in the Live environment. Those with newer systems such as mine will probably encounter issues such as this and are unable to even get into a Live environment (like I am working with).

---

### Post by demonicpagan on 2013-09-25
Well, I downloaded 13.10 and created a LiveUSB for it. Here are my findings:

[LIST]
[*]Will boot to Live enviornment ONLY when Secure Boot is ENABLED
[*]When in Live environment am unable to get the installer to run
[*]Selecting 'Install Ubuntu' from GRUB takes me to the installer but hangs after trying to continue past the 'Preparing to Install' screen (also has a glitch in the graphics)
[/LIST]

Another thing I noticed is that my wireless card is NOT detected in the Live environment. I have a Broadcom 802.11ac Network Adapter as my wireless card for this system. So, I'm still at a loss at trying to get Ubuntu installed on this system of mine.

Complete specs of my system ([https://www.asus.com/Notebooks_Ultrabooks/ASUS_ROG_G750JX/#specifications](https://www.asus.com/Notebooks_Ultrabooks/ASUS_ROG_G750JX/#specifications)):

Processor: Intel® Core&#8482; i7 4700HQ Processor

Operating System: Windows 8 Pro

Chipset: Intel® HM87 Express Chipset

Memory: DDR3L 1600 MHz SDRAM, 32 GB

Display: 17.3" 16:9 FHD EWV LED Backlight/Full HD 3D(1920x1080 120Hz) Non-Glare LCD Panel

Graphic: NVIDIA® GeForce® GTX 770M 3GB GDDR5 VRAM

Storage: 2.5" 9.5mm SATA, 1TB HDD 5400 RPM With 256 GB SSD 

Optical Drive: Blu-Ray DVD Combo, Super-Multi DVD, Blue-ray Writer

Card Reader: 2 -in-1 card reader ( SD/ MMC)

Camera: HD Web Camera

Networking: Integrated 802.11ac, 10/100/1000 Base T, BT 4.0 support (on WLAN+ BT 4.0 combo card)

Interface: 1 x Microphone-in jack
1 x Headphone-out jack (SPDIF)
1 x VGA port/Mini D-sub 15-pin for external monitor
4 x USB 3.0 port(s) 
1 x RJ45 LAN Jack for LAN insert 
1 x HDMI 
1 x mini Display Port
1 x Thunderbolt port (Optional)
1X AC adapter plug

Audio: Built-in 2 Speakers And Microphone
SonicMaster
Built-in subwoofer
MaxxAudio support

Battery: 8Cells 5900 mAh 89 Whrs

Power Adapter:
Output :
19.5 V DC, 9.23 A, 180 W
Input :
100 -240 V AC, 50/60 Hz universal
3/ 2 pin compact power supply system

Dimensions: 410 x 318 x 17 ~50 mm (WxDxH) (w/ 8cell battery)

Weight: 4.8 kg (with 8 cell battery)

Security: 
Kensington lock
LoJack
Intel Anti-theft

Note: Haswell-based laptops use DDR3 Low Power (DDR3L, 1.35V) memory modules. Install only DDR3L memory if upgrading.

---

### Post by oldfred on 2013-09-25
I recently had an issue with 13.10. Its icons use sh which should work. So I went into terminal copies command from properties of icon and changed sh to gksu bash. Sudo should not matter either, but that worked. But my system is an old BIOS system.

You may still need some other settings. Haswell systems have uses some or all of these possibly in addition to nomoeset or in place of it?
       acpi_osi=Linux  acpi_backlight=vendor

      
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by demonicpagan on 2013-09-25
I'll check into those, especially if they have any effect in getting the Live environment to recognize my Broadcom wifi card. That part right there is of utmost importance to have recognized. I'm sunk without it for internet access.

---

### Post by oldfred on 2013-09-25
The Broadcom issue should be a separate thread and I have seen many threads with that in the title.  All my systems just work.  Often you have to install with wired Ethernet and then download a new driver for wireless. 

You may want to search forum and if solution not found post details of your model in new thread.

---

### Post by demonicpagan on 2013-09-27
I will do that and see what I come across.

---

