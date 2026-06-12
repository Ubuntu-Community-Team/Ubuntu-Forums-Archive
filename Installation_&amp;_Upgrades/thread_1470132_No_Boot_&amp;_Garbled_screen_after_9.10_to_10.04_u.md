---
title: "No Boot &amp; Garbled screen after 9.10 to 10.04 update"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by rkraml on 2010-05-02
I am a real-time embedded programmer but still only marginally familiar with Linux.  I have had it installed on this laptop since version 7.xx and until now, the upgrades have essentially gone without a hitch.

So...   9.10 with latest updates was working fine.

I upgraded via update manger with no issues that I could see.  Upon reboot, I get a garbled screen and non-responsive system.  I can make out that there is some text but I cant read it.  Booting to recover console and safe graphics mode still results in garbled unresponsive  screen.  Just before the bad screen mounts I see a message flash by to the effect of nouveau something.

Note: booting to older Karmic 2.6.31.xx kernel still comes up OK with some new errors (something like: "cant mount none to /dev" and "initramfs not available") and still seems to still work although it is not as responsive as before.  Interestingly, as an aside, the Firefox menus don't work (!) but firefox itself does.

I also tried a new 10.04 install from Live CD  on new partition on same drive and it boots up OK but produces a lesser garbled but at least readable screen.  The arrow cursor has "noisy fuzz" around it and the screen borders have noisy pixels.

Dell Latitude D800 Laptop
internal nVidia Go 4200 at native LCD 1920x1200 resolution
1GB RAM, 1.GHz Centrino

---

### Post by cariboo on 2010-05-02
Try going to System->Administration->Hardware Drivers and install the correct restricted driver for your graphics chipset. if that doesn't cure the problem, start in recovery mode, hold down the shift key at the start of the boot, a grub menu should come up, use the arrow keys to select recovery mode. Once at the menu select drop to root prompt. At the prompt type:

```
nvidia-xconfig
```

once the above command has created a new /etc/X11/xorg.conf file, type at the prompt:

```
reboot
```

You should now be able to boot to a proper desktop.

---

### Post by rkraml on 2010-05-02
> **cariboo907 said:**
> Try going to System->Administration->Hardware Drivers and install the correct restricted driver for your graphics chipset. if that doesn't cure the problem, start in recovery mode, hold down the shift key at the start of the boot, a grub menu should come up, use the arrow keys to select recovery mode. Once at the menu select drop to root prompt. At the prompt type:

```
nvidia-xconfig
```once the above command has created a new /etc/X11/xorg.conf file, type at the prompt:

```
reboot
```You should now be able to boot to a proper desktop.
This is inteersting....

I tried to install the hardware drivers first.  It recommended nVidia v96 for my hardware and indicated it wasn't active.  I told it to switch to the recommended v96 driver and it went through its process and stopped with errors indicating it couldn't complete the operation and to look in jockey.log.  I looked at that file and there were a lot of debugs, warnings, and errors but one thing I saw over and over again was: nVidia 96 is not the driver to use.  There was also entries to the effect it was rebuiilding kernel images.  It did a lot of stuff.

However....   when I went to reboot, the system came up OK although it was proceeded by some low-res warnings about the hard drive not being ready and in general took a noticeably longer time to boot.  It seems OK though with the exception that Firefox menus still don't work.

Still going further, I tried the second suggestion with nvidia-xconfig after backing up the working xorg.conf file.  It emitted a bunch of warnings to the effect it could not locate mouse and keyboard but produced a new xorg.conf file.  However, when I rebooted, the display was readable but was EXTREMELY slow. Graohics took between 5 and 10 seconds to redraw.  When I was finally able to startup the Hardware Drivers app, it said "An Alternate Driver is in Use" and it still recommended v96.  Knowing what happened last time, i simply copied my last working xorg.conf back and rebooted.

One thing I should note here: I have never been able to get any Linux nVidia driver to work on this laptop so it is no surprise to me that it didnt work.  The recommended v96 driver is always unusalbly slow and I believe the newer one(s) I tried (back in the 9.04 or 8.xx days) didnt work at all.  Thus, I have always used the basic Ubuntu supplied driver and it has been OK since I never required 3d or compiz.

So.. now I am at least up and running again but my system still seems a bit sick in that it boots slowly, responds to desktop clicks slowl, and has a Firefox with non-working menu items.

---

