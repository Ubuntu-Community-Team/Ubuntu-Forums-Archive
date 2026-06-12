---
title: "Linksys USB Adapter Not Showing my Network"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kraken613 on 2010-04-07
I installed Ubuntu 10.04 earlier and I have a Linksys Dual-Band Wireless-N USB Network Adapter I use. I used it before in 9.10 and it worked fine. It seems to be working because it shows my neighbors unsecured network but my network that uses WPA2. 

I didn't know if there were any know solutions.

Thanks!

---

### Post by rbmorse on 2010-04-07
Is this a WUSB600N?   

I have one of those, worked great with Lucid (after installing a driver for the RT2680 chipset from the Railsys site) through either Alpha3 or Alpha4.  After that, it quit connecting to my network (WPA2), although it still sees the AP if I cilck on "show hidden networks" from the wireless tab of the network applett in the task bar. 

Bug 442178 in Lauchpad that mentions the issue and includes a work-around, but that has not been successful for me on Lucid (but I may have screwed something up).  

The original Bug report was for Karmic.  Comments already indicate it applies to Lucid, too, but I don't know if the Lucid bugtracker has picked this one up. 

It's a shame...this issue has pretty much moved me back to Windows 7 where the device is plug 'n play.

---

### Post by kraken613 on 2010-04-07
Yep, thats the one.... Too bad its doesn't work, I was looking forward to having it to use as a 2nd PC at my desk.

---

### Post by rbmorse on 2010-04-07
Well, as I mentioned before it worked fine through the Alpha versions of Lucid and I'm pretty sure that it will work again, someday.  But yes, it's a bit frustrating at the moment.

---

### Post by rbmorse on 2010-04-09
As of the latest updates, my Linksys WUSB600N adapter is working again and I have a WPA2 encrypted wireless link running at 130 Mb/s.

---

