---
title: "How do I downgrade?  Edgy is early beta quality"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by tz1 on 2006-12-23
When I last left Dapper, I had Google Earth running fine and I could close the lid on my notebook and it would take a while but come back up to the screen lock.

Now under Edgy, NOTHING works with the video card beyond the very basic features.  I have an Avaratec 3715 with a VIA Unichrome driver.  I had to update the drm modules manually to get Google Earth to work.  APM worked to suspend (and hibernation may have worked, but it would take a very long time).  Now not even Stellarium works (well, it technically does but takes several minutes to get beyond the splash screen instead of a few seconds), and the ext3 is set to fsck every 30 times - which means about twice a week since it won't recover every time I close the lid - I get a fractured display and a mouse cursor and have to cycle power.  V4L also locks things up when it tries to create an overlay.  The networking is also confused, I often have to do sudo -s and play with modules to have it find wireless networks.

And  you didn't put the EVDO usb modem patch in - I had to do that manually too, but at least I got that working.

I don't know why Ubuntu released "Edgy" as anything but an early beta, especially since I can't downgrade.  If someone has fixes to the above I'd like to hear about them, but I haven't found anything and the things I had to apply to Dapper to get it to work do nothing under Edgy.

Dapper at least worked right out of the install though a few tweaks helped.  I didn't expect Edgy to break nearly all my hardware and without the possibility of gettting it to work.

Can I just backup /home (and copy /etc so I can find things) and reinstall Dapper?  You should have a downgrade path when you release something this broken.

---

### Post by kalikiana on 2006-12-23
Did you see the sticky which warns you that Feisty Fawn is the unstable testing release? But seriously, since you seem to know that already you should have installed it on an extra partition. I don't see why there should be any way to downgrade from an unsupported release.

---

