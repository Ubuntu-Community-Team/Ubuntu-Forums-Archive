---
title: "Extremely slow boot (10.10) - hangs at blinking white dot"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by Nillerr on 2011-01-27
So I installed Ubuntu 10.10 yesterday, hoping to switch for good on my laptop.
I had some troubles installing it, but it eventually worked out.
Then I had to mess around with the grub.cfg file to remove screen on boot with the failed root stuff (the one where typing "exit" gets you past it), this worked out fine as well.
But when I managed to fix all of this, it would still hang at the flashing white dot on boot for 2-3 minutes.
I eventually gave up trying to fix this, and tried Ubuntu 9.10, which also had slow boot time, and then I just went and installed Windows 7.

Specs:
> Motherboard: Don't know
CPU: Pentium Dual Core T4300 @ 2.10 GHz
GPU: NVIDIA GeForce 9650 GT
RAM: 2x2 (4 GB)

When it would boot, WiFi worked as well.

Also read that you could switch something with the SATA controller in the BIOS, I didn't have the option that would fix it, I could only chose between AHCI and IDE, and AHCI was already chosen.

Since I would really like to switch to Ubuntu, what can I do to get fast boot times?

EDIT: Booting from the LiveCD works like I'd expect, fast and clean (well, as fast as my DVD drive allows...), it shows the Ubuntu loading screen without too many "white dots blinking" before it.
I'm using the 32-bit version.

---

### Post by Nillerr on 2011-01-28
Aren't anyone able to help me :/?

Is it a GPU issue? (I didn't update the drivers before I went to Windows 7)

---

### Post by Quackers on 2011-01-28
Well, seeing as both installations have now gone, it makes suggestions for a fix a little difficult.
First idea would be not to edit grub.cfg (as it says at the top of the file).
Another good idea would be to find out what was causing the flashing cursor problem (if it was actually a problem, and not just the boot process).

---

### Post by Nillerr on 2011-01-28
Without editing grub.cfg, the flashing cursor problem would just be split up between the "missing root info" screen (so there would be a flashing cursor before and after this screen), where the "exit" command gets your past it, editing grub.cfg was only to fix issues with that thing.
Since the system is relatively fast (it's not slow, that's for sure), it just doesn't make sense to me that the boot should take this long from the HDD, when booting a LiveCD takes well... less time :)
Do you believe that a fresh installation can fix it? I only tried going from 10.10 to 9.10, which also was slow at booting, but at least I got some pretty icon to look at while it was doing so (the white Ubuntu icon), which was distorted a little bit (like half a circle added to the top of the "circle").

Also, I had to reinstall Windows because I need the laptop for school work, and I didn't want to go into the whole dual-boot thing, because I'm not all that sure about it.

If I can only get some suggestions, I will try them out.

---

### Post by Quackers on 2011-01-28
All I can say is to try it again.
A flashing cursor at startup may be caused by installing grub to the wrong place. That is fixable within 10 minutes. It could possibly be a grpahics card issue.
But without a system installed to trouble-shoot, we're just guessing.
If you install again and the same thing happens, boot from the live cd/usb and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your new installation and may give clues to any problem.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

