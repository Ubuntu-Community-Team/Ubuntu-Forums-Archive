---
title: "Asus M5A97 LE R2.0 motherboard not booting Ubuntu 12.04"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by jobix on 2013-12-08
I'm having issues with the Asus M5A97 LE R2.0 motherboard. I put in a CD with Ubuntu 12.04-2 and went through the entire installation process, which took about an hour or so. At the end of that, the message on the LCD monitor said to remove any installation media and press "Enter." I removed the CD and pressed Enter. It booted up, gave a single beep as usual, and the lights on the mouse and keyboard lit up. But then nothing happens. CPU fans spins. LED light on motherboard is lit. But system does not boot up. Absolutely nothing shows on the LCD monitor. I tried putting in another disk (Ubuntu 13.10) and pressed Enter but nothing happens. A few times of rebooting and pressing "DEL" also does not get me anything. I don't even see the BIOS screen. 

Needless to say, this has been really frustrating. Any ideas on what I can do next? Any help would be very much appreciated.

Thanks.

---

### Post by fantab on 2013-12-08
Sounds like a RAM issue. Check it.
What kind of a machine do you have, laptop?
What Graphics Card is on the machine?

Can you boot with Live DVD and 'Try ubuntu without intalling'? 
If you can atleast see the boot menu when you boot from DVD, you will have an option under 'try ubuntu without installing' to test your RAM, called MEMTest...

---

### Post by jobix on 2013-12-08
Pretty sure it's not the RAM. It would've been beeping otherwise. A little while ago, i tried using a USB stick and this time it booted and for the first time, I was able to get into the BIOS. I changed the boot order to boot from CDROM, then hard drive, then flash drive. Hit "Save and Reset". Rebooted and this time, I was able to get in to my Ubuntu installation. Just to be sure, I removed the USB flash stick, and rebooted again. This time too no problem. I was able to get in to Ubuntu, open Firefox, etc. Then I shut down the computer for a while by physically disconnecting the power cable. Later when I connected and tried to boot, same old story - nothing whatsoever on the screen. I just cannot get into the BIOS, just like earlier. I hit all the DEL and ENTER keys but it just stays put. Removed all media, disconnected the hard drive, put in the USB flash stick and tried again but no success.

Why should it be so hard to get into the BIOS? :-(

I'm completely stuck.

---

### Post by fantab on 2013-12-08
Normally internal hardware issues prevent BIOS display... BIOS will load otherwise. 
You should pay attention to the 'beeps' and flashing 'LEDs' they indicate code. The MoBo OEM website/documentation will decipher the code for you... they generally have code-sheet with its meaning.

Is there a Windows in the picture?

---

### Post by jobix on 2013-12-09
I finally somehow managed to get to the BIOS again. Changed a setting that was set to "Windows"; changed to "Other OS". I believe it was somewhere in the UEFI related section. Also, instead of creating separate partitions like I had earlier, I decided to go with just a single one and loaded Ubuntu 13.10 on it instead of 12.04. No Windows or any other OS. Anyway, now it seems to be working. Was able to reboot a couple of times without problems. We'll see what tomorrow brings.

Thanks for the responses.

---

