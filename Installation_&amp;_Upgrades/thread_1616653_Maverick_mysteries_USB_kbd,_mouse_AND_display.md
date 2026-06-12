---
title: "Maverick mysteries: USB kbd, mouse AND display"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by GACurry on 2010-11-08
Needing a bit of insight here.

I have several machines which have been dual booting Ubuntu and Win for a couple years.   Not much problem with setting them up, and Ubuntu has been trouble free.

With this Maverick release, however, I've had quite a bit of trouble.   Having trouble characterizing the flakiness, but it persists on this machine as follows ...

I did a clean install of the 10/10/10 distribution, dual booting with Win 7.   Seemed to install OK and boot up once, although there might have been small problems during install, causing me to start over clean.

Machine is relatively new AMD X4 940, with ATI HD 4800 video.

The first flaky thing is that SOMETIMES (>50% of the time) the USB keyboard and/or mouse don't work (locked up).   Sometimes one does, but not the other, sometimes neither work.   I can't characterize why, but rebooting sometimes fixes it.   The Win 7 environment is fine.

The second flaky thing is that after the initial boot to the graphical desktop, more often I boot to the black login screen.   By reading this forum, I've found that "sudo service gdm start" usually starts the graphical desktop (although mostly with the mouse and or kbd frozen).

This is a clean install, with the proprietary ATI driver added.

I am dismayed, because this is so different from my earlier experience with Ubuntu.   Don't know if these problems are somehow linked, or quite how to proceeds.   Just looking for more stability.

---

### Post by coffeecat on 2010-11-08
I've nothing really coherent to suggest, except....

> **GACurry said:**
>  proprietary ATI driver added.

Was there a reason for adding the proprietary FGLRX driver? Unless you are a gamer, the default open-source ATI driver will probably be a better choice. I'm quite happy with the ATI driver with my Radeon HD4350 card. I get compiz too.

Did you have these troubles before you installed the proprietary driver, or did you do so too soon to be able to tell?

---

### Post by cariboo on 2010-11-08
Just to be sure, make sure usb-legacy is enabled in the BIOS. This does sound like more of a problem with the graphics driver, what are the contents of /etc/X11/xorg.conf?

If you remove the closed source drivers, do you still have the problem with the mouse and keybaord locking up?

---

### Post by GACurry on 2010-11-08
I'm running the experiment a bit tighter, this time.   I've re-installed 10.10 clean.   Installation went normally, restart went normally, no kdb or mouse problems so far.    But I will not make any changes this time until I've confirmed the normal behavior.   I'll get back here in a day or two with more data.

In the meantime, will double check the BIOS usb-legacy setting.   I've defaulted the conf file by reinstalling, so will have to wait on that question (actually, there is no file like that).

---

### Post by coffeecat on 2010-11-08
> **GACurry said:**
>  (actually, there is no file like that).

That's good. There is no (need for an) xorg.conf file with the open-source driver. Only the proprietary driver.

---

### Post by GACurry on 2010-11-08
Hmmm, well a bit more to report.   I have newly reinstalled 10.10, so am running a completely stock environment.  I wanted to try just repetitively rebooting the fresh environment to check on kbd and mouse.

In 4 of the 10, both kbd and mouse worked.  In 3, neither worked, and in the remaining 3, either the mouse or kdb worked.  It's weird because it seems so random.  Legacy USB in enabled in BIOS.

It feels like some boot time configuration race.   Interrupt conflict, or USB race of some kind.  Maybe I'll simplify my overall configuration to skeleton to isolate those issues out.

---

### Post by GACurry on 2010-11-08
Well, this is still mysterious.   I have a largish set of USB devices on the problem computer.   I unplugged a USB hub, with a remote control dongle on it, and unplugged a Seagate drive directly connected.

Then 10 more reboot cycles and 8 times had kbd and mouse.   Once, the boot didn't complete, and the time right after that, no kbd nor mouse.   Including the kbd and mouse, I have 8 USB devices hanging off this computer.   Wonder if that number could be aggravating my kbd and mouse lockups.

I just don't have a good theory for why my kbd and mouse are behaving, but it still feels like some boot time race problems.

---

