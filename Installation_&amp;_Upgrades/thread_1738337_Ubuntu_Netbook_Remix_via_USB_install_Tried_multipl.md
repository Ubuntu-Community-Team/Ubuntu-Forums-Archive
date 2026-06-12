---
title: "Ubuntu Netbook Remix via USB install? Tried multiple times, no luck"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by caspian915 on 2011-04-24
Hi all,

I have a new Samsung N145 netbook and I'm trying to load Ubuntu Netbook Remix on it via a USB stick (since I don't currently have a USB optical drive). I've tried Unetbootin, Universal USB Installer and Ultra ISO, and I've run into an issue every single time. One of the following:

* Once past BIOS, nothing but a cursor in the top left corner
* Booting into USB followed by BootMgr is Missing press CTRL + ALT + DEL
* Setup is booting from USB followed by SYSLINUX copyright line followed by computer restarting BIOS, doing that combo 4 times, then just getting stuck at the copyright line.

Possibly one other issue, but I can't remember.

Is there something holding these together? I have 1 partition currently with Windows 7. FWIW, I also have Jolicloud 1.2 installed, but inside Windows, not as a separate partition. Could that be the culprit? I wasn't trying to install UNR inside Windows, but rather on a new partition.

---

### Post by Dutch70 on 2011-04-24
Have you checked the md5sum of the downloaded .iso? 
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

Also, check the cd/usb for defects...
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

If those check out ok, try some other boot options like nomodeset. You may want to just try this first.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

It's also a good idea to select "Try Ubuntu" to make sure it runs on your hardware before installing.

---

### Post by caspian915 on 2011-05-01
The checksum checks out, and I've used this USB stick to install Windows 7 (after a few tries), so I don't think it's defective. The third suggestion, nomodeset, i'm not sure I entirely understand. The link seems to be telling me to pick something from the Ubuntu splash screen. I don't even get to the splash screen. The computer gets past the BIOS screen and then gives me a blinking cursor (when I use the Universal USB Installer). I've checked other threads about this, but none of the answers seem to be what I need.

What could I be doing wrong. I know this computer can handle Ubuntu, it's brand new.

---

### Post by Dutch70 on 2011-05-01
:) I didn't mean that the usb itself was defective, I meant to check the install that you put on it for defects. It shows up as "Check cd for defects" on the screen, but obviously you're not making it that far either.

However...It may actually be your usb stick.
Some USB sticks come with firmware that will prevent USB booting of Ubuntu from working. It's called U3. *(it's removable)*
[[COLOR="Red"]http://psychocats.net/ubuntu/usb[/COLOR]]("http://psychocats.net/ubuntu/usb")

---

### Post by caspian915 on 2011-05-01
Thanks for the suggestion. I'm pretty sure this USB stick doesn't have U3 on it--it wasn't advertised on the package, I don't recall when I first plugged it in, and I've done a complete format. Also, I'm guessing if it affected an Ubuntu install, it would have done the same for a USB install of Windows 7 and I was able to get that going. That took a few tries as well; didn't work with Unetbootin or Universal USB Installer, finally got Win 7 working with Ultra ISO; tried the last with Ubuntu, didn't work.

Is there anything else I can try?

---

### Post by caspian915 on 2011-05-01
Also, don't know if this adds anything, but when the system gets past BIOS and stays stuck at a blinking cursor, I discovered I can just take the USB stick out and Windows loads normally. However, very quickly before getting into the Windows loading screen, "Operating system failed to load" appears on the screen. I mean, that's kind of obvious, but maybe a clue to the kind of problem? I've just re-tried with Unetbootin and no luck. 

I'm using a USB stick because I have a netbook. Am I stuck with having to get a USB optical drive if I want to make this happen?

---

### Post by Dutch70 on 2011-05-01
For diagnostic purposes, if possible...
I would either try booting a different computer with your usb stick, or try booting your computer with a different usb stick. 

Unetbootin has no problems creating bootable usb sticks. That doesn't mean that you can't get a bad burn sometimes with any program.

There is a bug with some usb sticks, but I can't remember what it is.

If you're computer is capable, you can also try booting from a sandisk or memory card. The kind you use in a camera.

or an mp3 player...I've never tried this & you may find a better "how to" if you search for one.
[[COLOR="RoyalBlue"]http://www.ehow.com/how_6468806_make-live-bootable-linux-distro.html[/COLOR]]("http://www.ehow.com/how_6468806_make-live-bootable-linux-distro.html")

---

### Post by caspian915 on 2011-05-03
I gave up and bought an external optical drive. Oh well. But thanks for all the assistance.

- sps

---

