---
title: "Can't get ubuntu to work on my laptop."
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by jake87 on 2016-01-08
I am installing version 15.10 64 bit from a flash drive. I boot with the flash drive and choose install to this machine. It downloads then I get the prompt to restart my computer. Upon restarting it either boots from the flash drive or if I force boot from the hard drive it tells me to select a proper boot device.

Just ran the check disk and it found 2 errors in the files. The same copy of ubuntu was used on another computer and is working fine on it. Any idea what could be wrong?

---

### Post by Bucky Ball on 2016-01-08
*Thread moved to **Installation & Upgrades**.*

Welcome. You'll have more luck here and people will take into consideration you're new here. :)

It doesn't sound like you're removing the USB install media (as advised in the last screen of the install) or changing the BIOS to boot from the hard drive after the install. 

If the ISO is showing errors, you should re-download it whether it appears to be running ok on another machine or not, just as a precaution. You don't want something breaking unexpectedly further down the track.

The safest way to obtain the ISO is via a torrent. You will find the torrent files on the official Ubuntu site under Alternative Downloads> Bit Torrent.

---

### Post by jake87 on 2016-01-08
I've tried removing the install media and setting the the hard drive to boot from bios and it didn't work. I'll try reinstalling and get back to you. Thanks.

I tried torrenting the file and it also did not work. When should I remove the install media? When it prompts to restart?

---

### Post by Bucky Ball on 2016-01-08
Yes. It says there to remove the install media (in might be all USB media actually) and restart, unless something's been changed. What happens exactly when you reboot (and boot to the BIOS and change the boot device to the hard drive)?

---

### Post by jake87 on 2016-01-08
It tells me to select a proper boot device. If I have the hard drive saved as my primary boot device then it just boots into the flash drive unless I force it to use the hard drive in boot options, which gives me the select a proper boot device error. When it prompts for it to restart it says something like Installation complete. Restart your computer now to finish. I'll let you know exactly what it says in just a moment as I am trying it again. I'm trying to get Ubuntu 14.04.3 LTS to work now.

It says "Installation is complete. You need to restart the computer in order to use the new installation.".

---

### Post by Bucky Ball on 2016-01-08
Right, pull the USB dongle, reboot, enter BIOS, choose hard drive, continue.

Main thing, _pull the USB out_! Eliminate the option to boot from it after install.

---

### Post by jake87 on 2016-01-08
Same thing happened. "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key".

---

### Post by Geoffrey_Arndt on 2016-01-09
Post a screen shot of your hdd layout, using a live usb stick or dvd.   Plus, machine make and model, specs, etc. (especially gpu/graphics chipset).   Are running a machine that has uefi firmware instead of standard MBR bios?

---

