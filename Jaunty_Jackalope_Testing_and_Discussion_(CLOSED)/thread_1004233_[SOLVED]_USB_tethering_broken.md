---
title: "[SOLVED] USB tethering broken"
date: 2008-12-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by karvec on 2008-12-07
Using the latest alpha, I am having problems tethering my HTC Touch, and HTC Wing.

Not sure what to do, as rebooting with it plugged in works, but if I disconnect it and then plug it in again it no longer works.

Also, when trying to download torrent files, i.e. latest alpha iso or anything else, it seems to break the connection--  The connection on my phone will still be up and I will be able to access anything on the internet on my phone, and the internet sharing still says connected, but there is no network activity on linux-side.

Can't unplug and replug it in, as that breaks the connection and I then have to reboot.  Normal internet browsing works and downloading, but I am not able to use torrents at all, and as I usually leave it running overnight to grab the latest files, and my phone is my only source of internet (no internet at my barracks, USMC) I am S.O.L. any other way.  Was wondering if anyone had any ideas on what might be causing this--

I've restarted networking and NetworkManager to no avail, and not sure what else to try to fix this problem.

I really don't want to downgrade to fix this, as a fresh install of Intrepid was working fine, but I wanted to stay bleeding-edge...  And now I'm bleeding a little, so just trying to patch up the problem.

I'm not sure what to report this to launchpad as, because I don't know what packages are affected by it.

Thanks!!

---

### Post by ronacc on 2008-12-07
just report it as "unknown" and whoever triages it will assign it to the proper package . But now of course I Have to give you lecture #742 about upgrading your only install to an Alpha , bad idea, breakage is 100% certain.

---

### Post by karvec on 2008-12-08
Fixxed it, removed synce and installed the usb-rndis-lite...

really think it had to do with synce more than anything else, but it works 4x faster now, so glad I used usb-rndis-lite also.

---

