---
title: "Upgrade to Edgy"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2006-11-05
Hi,

Just upgraded to edgy eft from dapper.  No major problems.

Firestarter broke and had to be completely uninstalled and reinstalled manually using
```

sudo aptitude remove -fy firestarter
```

then

```
sudo aptitude install -fy firestarter
```

so far, so good... Edgy looks nice

---

### Post by andril on 2006-11-05
I attempted to log into my Gnome Desktop after my update to Edgy Eft and was left on a blank screen. I then logged in via KDE (working fine) and created a new user & uninstall Beryl - logged in with new user in Gnome and all was fine. Is Beryl ready for Edgy???](*,)

---

### Post by rfruth on 2006-11-05
Fx2 is a dream !

---

### Post by NeoLithium on 2006-11-05
I didn't have any problems either; it's kind of nice that a few of us seem to be lucky; and it's running at phenominal speed with the new kernel that I just compiled.

---

### Post by Kateikyoushi on 2006-11-05
> **andril said:**
> I attempted to log into my Gnome Desktop after my update to Edgy Eft and was left on a blank screen. I then logged in via KDE (working fine) and created a new user & uninstall Beryl - logged in with new user in Gnome and all was fine. Is Beryl ready for Edgy???](*,)

Edgy has Aiglx built in that might cause problem, I can use beryl on it.

---

### Post by ezaron on 2006-11-07
On an IBM T30 laptop with ATI/radeon mobile 7500:

Upgraded to Edgy (from Breezy) with almost no problems.

Issues:
1) The wireless card doesn't always work (request_netdev fails in dmesg). The built-in wireless card is a cisco aironet. To fix this I manually
sudo modprobe -r airo airo_cs
sudo modprobe -v airo_cs
to force a reload of the driver. To configure the card properly and use it I do
sudo ifdown -a
sudo ifup -a
to reset network interfaces

>>> PERMANENT FIX: The pcmcia init.d script seems to be unnecessary (according to the pcmcia-utils man page), but it is still listed in /etc/rcS.d/ so I renamed the script (was S40pcmcia) to X40pcmcia. Now the internal wireless card works fine after boot-up.

2) Slow scrolling in web browser and some other stuff seems a little slower.
I guessed that the video card wasn't being used properly. Indeed, looking at /etc/X11/xorg.conf I saw no mention of my video card. To fix:
reboot in recovery mode (no Xserver running)
Xorg -configure
This results in an error (it can't find my touchpad mouse), but it does find the correct video card and writes its results to /root/xorg.conf.new.
Then I copy the "Device" portion of /root/xorg.conf.new to my regular xorg.conf file, naming it xorg.conf.next, until I have tested it out.
Test the new configuration with
X -configure xorg.conf.next
Diffing against an old xorg.conf, I see the old version did a "Load GLcore", so I add this too. Then rename xorg.conf.next to xorg.conf and reboot.

Everything seems to work great! Thanks a lot for putting this distribution together!

-ed

---

