---
title: "Booting from USB problem, need assistance"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by cNicely on 2012-03-16
Just spent the last 3 hours in my skivvies putting together my new PC and it all just came to a screeching halt, so I put some clothes on and came here for help. 
 
Specs: 
i5 2500K : CPU
Asus P8Z68-V Pro : Motherboard
EVGA GeForce GTX 560 TI : GPU
 
8GB 1600 ram, 550 watt PSU, 128gb SSD, etc etc etc
 
Formatted my USB stick (8GB) using pendrivelinux to make the iso image bootable. Power on computer, get to Asus' awesome new BIOS screen, everything looks good so far. Recognizes both the SSD and the USB. Boot from USB, next screen has an Ubuntu splash and options such as "Boot from this USB device" "Install Ubuntu on a hard drive" etc. Any option that I choose, will throw me into what looks like a command prompt, shooting down 100 or so lines then just stop. 
 
With that | cursor just blinking, mocking me for my failure. 
 
If anyone could shoot me in the right direction I would be very grateful, haven't built a PC since I was about 14, and it ain't like riding a bike.

---

### Post by cNicely on 2012-03-16
Specs: 
i5 2500K : CPU
Asus P8Z68-V Pro : Motherboard
EVGA GeForce GTX 560 TI : GPU
 
8GB 1600 ram, 550 watt PSU, 128gb SSD, etc etc etc
 
Running into an issue trying to boot Ubuntu on my new PC. Formatted my USB stick (8GB) using pendrivelinux to make the iso image bootable. Power on computer, get to Asus' awesome new BIOS screen, everything looks good so far. Recognizes both the SSD and the USB. Boot from USB, next screen has a black/white Ubuntu splash and options such as "Boot from this USB device" "Install Ubuntu on a hard drive" etc. Any option that I choose, will throw me into what looks like a command prompt, shooting down 100 or so lines then just stop. 
 
 
With that | cursor just blinking, mocking me for my failure. 
 
Any help would be greatly appreciated.

---

### Post by darkod on 2012-03-16
Do you have any chance to create the usb on another ubuntu machine? Using third party tools can mess up the main menu, losing some of the options.

For example, you mentioned it has Install option, but what about Try ubuntu? That is what you need to run first to see how it goes.

This seems like a video issue. If the usb was created on ubuntu, with normal menu, you would do:
As soon as the first purple screen shows, hit Esc. That should bring on the older main menu. Hit F6 for Advanced options, select nomodeset. Select the Try Ubuntu option in the main menu.

If that can load the live mode, you can install but note that on first boot the same problem will happen unless you edit the boot file to include nomodeset. After it boots once you can install the video drivers and it should be fine, or if that doesn't help you can make the nomodeset fix permanent.

---

### Post by cNicely on 2012-03-16
I only have access to my Macbook and my roommates Windows PC. 
 
There is not an option to "Try Ubuntu" in the options I am getting after the BIOS screen. Not sure what to expect from that initial boot screen, but it's a low resolution, black and white Ubuntu logo with the options I stated above. There is an advanced options choice but nothing within it except to go back to the previous options.

---

### Post by oldfred on 2012-03-16
You need to hit a key as soon as the CD/USB starts.

I think every nVidia requires the nomodeset setting to boot the liveCD and boot the first time until the nVidia proprietary drivers are installed.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

### Post by s.fox on 2012-03-16
Duplicate threads merged.

Please only create one support thread per query.

Thank you.

---

### Post by cNicely on 2012-03-16
Thanks oldfred, I don't remember seeing any key prompts before the Ubuntu screen, but this motherboard does have an integrated GPU, so I think I will bypass the 560 ti for now, install all necessary drivers, then give it another go once I actually have Ubuntu installed on the system?

---

### Post by darkod on 2012-03-16
Don't expect any prompts. There is no message that tells you you can access the older type of main menu by hitting a key.
Just boot, and after POST ends hit Esc few times. I can't be sure it will work because it might depend how the usb was created and whether pendrivelinux is making changes to the boot process. That's the main question. If changes were made, maybe you can't expect the result to be the same.

---

