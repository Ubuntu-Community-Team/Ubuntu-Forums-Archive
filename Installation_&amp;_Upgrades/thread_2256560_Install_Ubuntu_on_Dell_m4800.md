---
title: "Install Ubuntu on Dell m4800"
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by Alfahham on 2014-12-13
Hi 

I have Dell m4800 with win8 and I want to install Ubuntu. I tried to install from usb many times but I failed. each time after change the boot sequence and enter to install screen and press install the screen turn black and nothing after that. would you please guide me to install Ubuntu cause I need it to much.
the specifications are:

BIOS:  A05

Processor: Intel core i7-4900MQ 2.8GHz

Memory : 16GB

VGA: NVIDIA Quardro K2100M

thank you

---

### Post by sudodus on 2014-12-13
Welcome to the Ubuntu Forums :-)

Which version of Ubuntu are you installing?

I guess you are running in UEFI mode. See these links

[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[/URL]  			 			[URL="http://ubuntuforums.org/showthread.php?t=2147295"]
UEFI Installing - Tips[/URL] 				


Often there are problems with the built-in graphic driver and nvidia. It might help with the boot option **nomodeset**, that you add according to the following link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

When things work at least at a basic level, you can try installing a proprietary driver for nvidia.

---

### Post by Alfahham on 2014-12-14
Hi 

Many thanks for warm welcoming to the Ubuntu Forums.
I try to install 14.04 
the problem is I stopped the UEFI as many tags suggest and boot from usb, an option page appears and when I choose install Ubuntu the usb flash flashes many time but the screen turn to black and nothing after that.

Is there any special format for the usb or any thing that I may miss out? I don't know.

---

### Post by sudodus on 2014-12-14
Do you want a dual boot system with Ubuntu and Windows?

I suppose Windows is running in UEFI mode. This means that you should install Ubuntu in UEFI mode too, and you need to use the tips in the links in my previous post. (If you install Ubuntu without UEFI, you must enter the UEFI/BIOS menu system each time you want to switch between Windows and Ubuntu, which is rather inconvenient.)

You may also have problems with the graphics (typical with nvidia graphics until you install a proprietary driver).

1. Please explain in detail, what happens when you try to boot from the installed system.

2. Please explain in detail, what happens when you try to boot from the Ubuntu install drive (flash drive).

---

### Post by Alfahham on 2014-12-14
First of all 
thank you for quick response.

yes I want a dual boot with Ubuntu and Windows and my windows is running in UEFI:

first I download the Ubuntu 14.04 and made a bootable USB.
then I turned fastboot in win8 off.
then I turned UEFI off. 
then reboot and choose a usb as boot device then from page that say try Ubuntu, install Ubuntu ,.....etc 
I chose install Ubuntu.
the screen turn black every time and no thing after that. I waited for 30min hopping that my be installing in background but no use.

---

### Post by sudodus on 2014-12-14
I suggest that you re-install Ubuntu (64-bit) while in UEFI mode. Select ***Something else*** at the partitioning page (and re-use the Ubuntu partition).

It might work directly at reboot. If problems, try **Boot Repair** (booted from the pendrive).

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Alfahham on 2014-12-16
Hi 

Which ubuntu should I use i368 or AMD64.

regards

---

### Post by sudodus on 2014-12-16
Only AMD64 works with UEFI.

See these links

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295")

---

