---
title: "Issue installing Ubuntu on MSI GE62 Apache Pro-004"
date: 2016-03-04
forum: Installation &amp; Upgrades
---

### Post by rolltide101x on 2016-03-04
I have this laptop and am getting these errors when trying to boot Ubuntu from USB.


[http://www.bestbuy.com/site/msi-ge62-apache-pro-004-15-6-laptop-intel-core-i7-16gb-memory-1tb-hard-drive-aluminum-black/4556202.p?id=1219766811085&skuId=4556202](http://www.bestbuy.com/site/msi-ge62-apache-pro-004-15-6-laptop-intel-core-i7-16gb-memory-1tb-hard-drive-aluminum-black/4556202.p?id=1219766811085&skuId=4556202)


Before when I tried to boot from USB I got a "CPU lockup" error but I do not get far enough into the boot now to get that error. Please see pictures for exact error messages. Sorry for the flash but it did not want to focus on it well without the flash for some reason.

Just let me know of anything you want me to try. I really would like Ubuntu on this PC as Ubuntu has been my primary OS for years but I keep Windows around for gaming :p




**EDIT: **I added "nomodeset" and "idle=nomwait" and the live usb did boot to 800x600. Anybody have any further ideas on what to do to get it to work at full resolution?

---

### Post by rolltide101x on 2016-03-04
This is what happens when I only add "idle=nomwait"

[https://drive.google.com/file/d/0Bwz4EYsvC0acMkdlU09kYnY0VHMzVGppcWd1Z0oxd3E3SDZV/view?usp=sharing](https://drive.google.com/file/d/0Bwz4EYsvC0acMkdlU09kYnY0VHMzVGppcWd1Z0oxd3E3SDZV/view?usp=sharing)

BUG: soft lockup - CPU#5 stuck for 23S


Any ideas?

---

### Post by rolltide101x on 2016-03-05
I managed to get Ubuntu to boot and install it and afterwards get it to full resolution. This worked with Ubuntu 16.04 Mate Beta 1 (Wireless does not work correctly in 15.10)

Steps 

Load the live usb/cd and on the Grub menu add "nomodeset" and "idle=nomwait" to the boot. (This will allow you to boot into Ubuntu at 800x600)

Install Ubuntu as normal to the HDD

After the install you must add "nomodeset" and "idle=nomwait" to the boot again when you boot it from the HDD

Boot Ubuntu up and install the Intel Driver and Nvidia Driver from "additional drivers"

[https://drive.google.com/file/d/0Bwz4EYsvC0aceS1RV2JoRko0OWs/view?usp=sharing](https://drive.google.com/file/d/0Bwz4EYsvC0aceS1RV2JoRko0OWs/view?usp=sharing)


Then you need to permanently add "idle=nomwait" to your grub bootloader, nomodeset is no longer needed.


After that you will have a working desktop at 1080p.    Only issues I know of (which I am working on) is I can not seem to switch to the Intel APU for graphics and you must keep "idle=nomwait" into the bootloader for it to boot.


Hope this information helps someone

---

### Post by sergy8612 on 2016-03-24
Hi,

I just ran into the same problem. I purchased an MSI GE72 6QD without OS and tried to install 15.04 from an USB stick. 
I followed these steps to SOLVE the problem :

1. Enter BIOS mode when booting by pressing DEL key and set this:

[LIST]
[*]Intel SpeedStep --> off
[*]Intel Virtualisation stuff --> off
[*]Fast boot --> off
[*]Secure boot --> off
[*]Boot mode --> UEFI with CSM
[/LIST]


2. When rebooting from usb stick, on grub display press "E" key to edit options to pass kernel on boot(in my case with the option "try ubuntu without installing" marked). 
In the line starting with linux I added the options "nomodeset idle=nomwait". Then press F11 to load kernel with these options. It worked and I could install Ubuntu.    

Just as said [**[COLOR=#000000]rolltide101x[/COLOR]**]("http://ubuntuforums.org/member.php?u=1270233") when booting from HDD I had to repeat step 2 to boot properly. Thank you for your help!!

---

### Post by X-RED_Tech on 2016-03-24
15.04 is already out of support, it shouldn't be used.
Also it shouldn't be necessary to turn off secure boot nor enable legacy mode. The other options have reasons to be turned off but the ones I mentioned you just did wrong. And, of course, for newer hardware, newer versions.

---

### Post by sergy8612 on 2016-03-25
True! I'm using 15.10 and not 15.04, I was wrong in my previous post. But when installed I had to enable legacy mode to be able to enter grub and boot. In UEFI mode the laptop,  enter inmediately to BIOS. And I installed everything automatically from the USB installer for 15.10 using UEFI with CSM. Can this be due to an old version of GRUB?

---

### Post by rolltide101x on 2016-03-27
Do you have screen tearing at all? I can not seem to fix that issue. About to try to upgrade the kernel to 4.6 RC1 and see if that helps

---

### Post by sergy8612 on 2016-04-06
Hi,

my kernel has been updated automatically to 4.2.0-35 on Ubuntu 15.10. Therefore grub.cfg has been updated and I had to pass again the option **idle=nomwait **to the kernel to be able to boot.

Do you know why I have to pass this option? Have you had similar problems in other models of computers?

---

### Post by gentra-a on 2016-04-26
My system has run almost fully-stable right now I think.
I added this on Ubuntu GRUB kernel options: "nouveau.modeset=0"

I think it will make the nvidia driver not working. But it's not really a problem for me since I only use this OS for work and playing games on Windows

---

### Post by sergy8612 on 2016-10-11
Hi,

I just wanted to point out that with ubuntu 16 LTS with his new kernel this problem is not longer present.

However, chances are still high to have this very problem if you try to install ubuntu 16+ from the usb stick for example when booting in test mode without installing, then you need edit the grub entry of teh USB (pressing TAB) and add "nomodeset idle=nomwait" to boot. Today I had this problem again when trying to reinstall ubuntu 16 LTS on mi MSI laptop from a usb stick made with the latest ubuntu amd image and the program from pendrivelinux. 

I still have no idea why "nomodeset idle=nomwait"

---

### Post by sergy8612 on 2016-10-11
Hi,

I just wanted to point out that with ubuntu 16 LTS with his new kernel this problem is not longer present.

However, chances are still high to have this very problem if you try to install ubuntu 16+ from the usb stick for example when booting in test mode without installing, then you need edit the grub entry of teh USB (pressing TAB) and add "nomodeset idle=nomwait" to boot. Today I had this problem again when trying to reinstall ubuntu 16 LTS on mi MSI laptop from a usb stick made with the latest ubuntu amd image and the program from pendrivelinux. 

I still have no idea why "nomodeset idle=nomwait"

---

