---
title: "Bios Upgrading"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by Biosd on 2010-12-10
Okay I have a toughie for the experts.

I have a Compaq Presario SR1300, and I wanted to install Ubuntu 10.04 server on it with wireless capability from my Alpha Network card. The problem is that when I plugged it in, the light on the card didn't turn on (indicating that the computer didn't accept it). I assumed this might be a BIOS problem and I want to upgrade the BIOS.

I went over to HP's website to get the updated driver, but the problem is that its for Windows XP. I don't own any Win XP disks...

Any ideas? Or am I moving in the wrong direction?

---

### Post by tommcd on 2010-12-10
First off, the new BIOS is not a "driver". 
BIOS files are usually something like *new-bios.bin* or similar.
Are you trying to install a driver for your network card, or are you trying to update your motherboard's BIOS??
These are two completely different things.
Also, updating the BIOS is dependent on how your hardware manufacturer makes the BIOS updates available. 
For example, Gigabyte supplies their BIOS updates as Windows .exe files that must be extracted with cabextract as far as I know:
[http://www.cabextract.org.uk/](http://www.cabextract.org.uk/)
On the  Asus M2N SLI Deluxe motherboard in my sig, I recently updated the BIOS with a floppy disk that was formatted to fat32 that had the new BIOS file on it. I used linux to make the floppy and load the BIOS file to it. This is one reason why I like Asus motherboards.
Can you post a link to your manufacturer's BIOS update procedure?
Or if you just want a driver for your network card, post a link to that info.

And welcome to the Ubuntu forums!

---

### Post by Biosd on 2010-12-10
no. I am not looking for a driver. I need to update BIOS to the computer to recognized whats being plugged into the USB. The driver is there (RTL8187), the BIOS won't recognize it.

[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=228&lc=en&cc=us&dlc=en&sw_lang=&product=443734](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=228&lc=en&cc=us&dlc=en&sw_lang=&product=443734)

---

### Post by tommcd on 2010-12-11
> **Biosd said:**
> no. I am not looking for a driver. I need to update BIOS to the computer to recognized whats being plugged into the USB. The driver is there (RTL8187), the BIOS won't recognize it.

Are the usb ports enabled in your current BIOS? 
The info on the new BIOS you linked to does not mention anything about enabling usb ports:
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-31037-2&lc=en&dlc=en&cc=us&os=228&product=443734&sw_lang=](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-31037-2&lc=en&dlc=en&cc=us&os=228&product=443734&sw_lang=)
Do you still have Windows on the laptop? If so, then just download the BIOS.exe file and flash the BIOS as per the instructions on the page you linked to.
If you have Ubuntu on the laptop, first plug in the wireless card then run **lsusb** in the terminal to see if Ubuntu detects the wireless device.

---

### Post by Biosd on 2010-12-11
Its actually a old Desktop computer.

The USB ports seemed to work when I plug in a USB drive, but when I plug in my ALFA, it seems not to work.

No, The system has no Operating system at this time.

---

### Post by tommcd on 2010-12-11
> **Biosd said:**
> 
No, The system has no Operating system at this time.
Well if the computer has no OS, then how can you be sure that Ubuntu does not see the wireless device?
Why don't you try running a Ubuntu live CD and open a terminal and run **lspci** and **lsusb** and see if Ubuntu detects the wireless.
After Ubuntu is installed there may be a driver that you would need to install to get the wireless working if it does not work out of the box.
Also, if everything else you plug into the usb ports seems to work and the wireless device does not, are you sure the wireless device is not defective? The usb ports must be functioning if you can plug a usb drive into them and have it be detected. I doubt that a BIOS update would make the wireless device light up, especially since the info on the HP support page you linked to has no mention of usb ports listed in the BIOS update.
I had a similar issue with my laptop. Unless a certain driver was loaded my wireless card would not light up when I plugged it into the pcmcia slot. I can't remember the name of the driver at the moment, but it was needed to get the pcmcia slot to function.

---

