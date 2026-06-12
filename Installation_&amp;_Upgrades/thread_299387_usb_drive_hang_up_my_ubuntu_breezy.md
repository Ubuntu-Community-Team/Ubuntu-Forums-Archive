---
title: "usb drive hang up my ubuntu breezy"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by annes on 2006-11-14
I have installed ubuntu 5.10 breezy. when I plug my flash drive on my pc, it will suddenly goes hang up. I don't even get any error message on the log file. Is there anyone facing the same problem?Thx for the answer.

--jo--

---

### Post by bpollen on 2006-11-14
In my case, with Dapper, boot will hang with USB drive(s) attached.
AFTER boot, however, the OS recognizes any of my USB drives when connected, and recognizes when they are removed.....

---

### Post by annes on 2006-11-14
I don't have booting problem if I attach any usb drive. My Ubuntu will recognize my usb drive only if I attached before booting.](*,)

---

### Post by joshuapurcell on 2006-11-30
I've had major problems with USB on both Dapper and now Edgy on two different desktop using the same three USB devices: a basic keyboard (forgot the brand), an older Logitech optical mouse, and a Linksys WUSB54GV2 (using the latest ndiswrapper and associated Windows drivers). Now I can boot just fine with any or all of the three devices plugged in, and there are never any errors in the logs or on-screen. I can even successfully use the wireless adapter on either desktop (I used it as my primary connection for my laptop running Ubuntu for months). But almost as soon as I have all three devices plugged in to these two desktops I've tried this on AND I start pulling data from the network using the wusb54g (usually by starting up an FTP transfer or opening Firefox), my computer hangs completely. With this much new and much faster computer that I currently have, the hang doesn't happen as fast; sometimes only the desktop will hang with no clicking anywhere having any affect (but the clock and mouse still work).

I have looked all over the internet and found nothing that explains why this is happening. I would be ok with the fact that there is something wrong with using a Windows driver (via ndiswrapper) that is causing this problem, but I have had much success in using this exact same device in other computers while using the exact same OS and other software and drivers to interface with it. I'm tempted to install Gentoo and then use these same three devices and see if the same hangin occurs there. I'm not sure where that would leave me if I had success or failure, since I still would not know where the problem was in Ubuntu. Again, I'm able to use any one of these devices without any problem, just combined I have hanging problems. Is there some sort of problem with how USB devices are handled in Ubuntu? If anyone has any information on this possibility, then some links would be very much appreciated.

---

