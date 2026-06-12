---
title: "Ubuntu 10.10 desktop + Acer Aspire One 753 = problem"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by LaMpiR on 2011-01-31
Hey guys,
I tried once again to start using ubuntu. I've downloaded the version for desktop 32bit. Checked md5 for *.iso file. I've tried many version on installing:
1) mount with ultraiso and run wubi. Kept getting error that I have no cd and I just clicked continue and after 10 clicks it gives me install windows. Used 10gb of space on C: drive. Everything was done. Booted, login screen is terminal. No what so ever graphical interface. Tried startx, /etc/init.d/gdm start but it gives me only black screen and that's it. It lead to no where.
2) mount with ultraiso, used usb creator, restarted pc, only get Syslinu v3.02 etc... first line and it get's stuck there.
3) Used Universal USB installer. Reserved 10gb of space ext3/4 but no luck. Still only terminal, no startx of gdm start so no luck. I got to the login screen before installing, and i've done everything but restart, nothing happened. 
4) Used UUI but made updates download as I configured my connection. I have usb dongle for hsdpa connection.
No luck once again.

Can You please give me some options here? I was at some point able to find out that I have no xorg.conf so I've found one somewhere online, I think it was ubuntu support but it started. It didn't look like much to be honest.
Isn't there some tool to create xorg.conf according to my pc components? 
Currently installed is number 4 but only terminal with startx and black screen.

Please help me :)

---

### Post by LaMpiR on 2011-01-31
I've googled a bit about this and created black-intel_ips file. It resolved my problem with interface.

I have now problem with slow internet. I have Drei(3) in Austria and it's working in HSUPA mode only while in windows it's working in HSDPA. I have ZTE MF 112 usb dongle.
This results in slooow connection.
Is there anyway to improve this?

---

