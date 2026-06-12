---
title: "Can't boot Karmic Alpha 6 from USB Hard drive"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rockyjones on 2009-09-21
I installed Karmic Alpha 6 on a 80 Gig hard drive plugged directly into my Thinkpad T-60.  Works fine.  This was a spare hard drive I have for testing.  I have Jaunty installed on a 160 gig drive that is normally installed in the T-60.  I subsequently removed the 80 gig Karmic drive and installed it into a portable USB case so I could boot it when I wanted to test from USB.  Unfortunately, Karmic won't boot from the USB hard drive.  It boots fine if I plug it into the T-60 "bus".  I removed the jaunty drive from the T-60 and put it into the portable USB case then put the Karmic drive back in the T-60 and the jaunty usb drive boots fine.  Tried booting the Karmic drive from USB with no drive in the T-60 and it does the same thing.  The Jaunty drive boots from USB with or without the Karmic drive installed in the T-60.

Anyone know why Karmic won't boot from a USB hard drive?  It hangs about half way through the boot with a whirling cursor and remains forever.

Joe

---

### Post by rockyjones on 2009-09-21
Well, looking at Syslog, I see that the wireless connection completed then it hung with the following (excerpt from syslog)....

Sep 21 20:21:31 LittleDog NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Sep 21 20:21:33 LittleDog ntpdate[2509]: adjust time server 91.189.94.4 offset 0.025826 sec
Sep 21 20:21:41 LittleDog wpa_supplicant[1894]: CTRL-EVENT-SCAN-RESULTS 
Sep 21 20:22:21 LittleDog wpa_supplicant[1894]: CTRL-EVENT-SCAN-RESULTS 
Sep 21 20:23:21 LittleDog wpa_supplicant[1894]: CTRL-EVENT-SCAN-RESULTS 
Sep 21 20:24:41 LittleDog wpa_supplicant[1894]: CTRL-EVENT-SCAN-RESULTS 
Sep 21 20:26:21 LittleDog wpa_supplicant[1894]: CTRL-EVENT-SCAN-RESULTS 
Sep 21 20:28:22 LittleDog wpa_supplicant[1894]: CTRL-EVENT-SCAN-RESULTS 
Sep 21 20:30:21 LittleDog wpa_supplicant[1894]: CTRL-EVENT-SCAN-RESULTS 

And the last lines are repeated until I power off.

I'm relatively new to Linux and don't really know what this might be.  Anyone??

Joe

---

### Post by oboedad55 on 2009-09-22
> **rockyjones said:**
> I installed Karmic Alpha 6 on a 80 Gig hard drive plugged directly into my Thinkpad T-60.  Works fine.  This was a spare hard drive I have for testing.  I have Jaunty installed on a 160 gig drive that is normally installed in the T-60.  I subsequently removed the 80 gig Karmic drive and installed it into a portable USB case so I could boot it when I wanted to test from USB.  Unfortunately, Karmic won't boot from the USB hard drive.  It boots fine if I plug it into the T-60 "bus".  I removed the jaunty drive from the T-60 and put it into the portable USB case then put the Karmic drive back in the T-60 and the jaunty usb drive boots fine.  Tried booting the Karmic drive from USB with no drive in the T-60 and it does the same thing.  The Jaunty drive boots from USB with or without the Karmic drive installed in the T-60.

Anyone know why Karmic won't boot from a USB hard drive?  It hangs about half way through the boot with a whirling cursor and remains forever.

Joe

Okay, I'll take a stab at this. Was karmic installed on a secondary drive? If so, when you switch it to boot up by itself there's no mbr, which is on the first drive. So, you'd need to install grub on the karmic drive as well to get it to boot up.

---

### Post by rockyjones on 2009-09-22
Nope... installed on the drive having the problem which was inserted into the T-60 (NOT usb connected) and the only drive in the machine.  

As I mentioned, when I put this drive in the T-60's hard drive slot, it boots up fine and Karmic runs fine.  It just won't boot fully when I put it in a portable USB enclosure and try to boot it with it plugged into a USB port.  However, the other drive just like it (2.5" 160 gig) that I run Jaunty on will work either in the portable enclosure booting from a USB port or inserted into the T-60 drive slot.

---

### Post by shid007 on 2009-10-02
I think that I have the same problem with Karmic beta as you... I think it's grub2 related... I'll try to install legacy grub and post what will happen...

Edit: it doesn't work either...

---

