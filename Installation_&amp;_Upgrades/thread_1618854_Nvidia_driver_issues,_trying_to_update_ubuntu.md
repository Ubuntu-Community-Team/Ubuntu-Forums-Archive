---
title: "Nvidia driver issues, trying to update ubuntu"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by Cyked on 2010-11-11
So I'm trying to update my box and running into issues.  I ended up leaving it doing its thing last night after going to bed.  I walk into the den this morning with out of memory errors, no available processes to kill, or something to that affect on the screen and the caps and scroll lock lights on the keyboard blinking.

I reboot and end up a command prompt login.  After playing around with it for about an hour I haven't been able to get anywhere.  I have been able to boot up once in minimal graphics mode.

Right now in the kernal log here is what I see:

```
Nov 11 01:07:58 tux kernel: [   39.303840] NVRM: No NVIDIA graphics adapter found!
Nov 11 01:07:59 tux kernel: [   39.590814] NVRM: The NVIDIA GeForce4 MX 440 with AGP8X GPU installed in this system is
Nov 11 01:07:59 tux kernel: [   39.590819] NVRM:  supported through the NVIDIA 96.43.xx Legacy drivers. Please
Nov 11 01:07:59 tux kernel: [   39.590821] NVRM:  visit http://www.nvidia.com/object/unix.html for more
Nov 11 01:07:59 tux kernel: [   39.590823] NVRM:  information.  The 185.18.36 NVIDIA driver will ignore
Nov 11 01:07:59 tux kernel: [   39.590825] NVRM:  this GPU.  Continuing probe...
Nov 11 01:07:59 tux kernel: [   39.590834] NVRM: No NVIDIA graphics adapter found!
Nov 11 01:07:59 tux kernel: [   39.943121] NVRM: The NVIDIA GeForce4 MX 440 with AGP8X GPU installed in this system is
Nov 11 01:07:59 tux kernel: [   39.943127] NVRM:  supported through the NVIDIA 96.43.xx Legacy drivers. Please
Nov 11 01:07:59 tux kernel: [   39.943129] NVRM:  visit http://www.nvidia.com/object/unix.html for more
Nov 11 01:07:59 tux kernel: [   39.943131] NVRM:  information.  The 185.18.36 NVIDIA driver will ignore
Nov 11 01:07:59 tux kernel: [   39.943133] NVRM:  this GPU.  Continuing probe...
Nov 11 01:07:59 tux kernel: [   39.943141] NVRM: No NVIDIA graphics adapter found!
Nov 11 01:07:59 tux kernel: [   40.279955] NVRM: The NVIDIA GeForce4 MX 440 with AGP8X GPU installed in this system is
Nov 11 01:07:59 tux kernel: [   40.279961] NVRM:  supported through the NVIDIA 96.43.xx Legacy drivers. Please
Nov 11 01:07:59 tux kernel: [   40.279963] NVRM:  visit http://www.nvidia.com/object/unix.html for more
Nov 11 01:07:59 tux kernel: [   40.279965] NVRM:  information.  The 185.18.36 NVIDIA driver will ignore
Nov 11 01:07:59 tux kernel: [   40.279967] NVRM:  this GPU.  Continuing probe...
Nov 11 01:07:59 tux kernel: [   40.279982] NVRM: No NVIDIA graphics adapter found!
```


And in the xorg log:

```
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

Not sure where to go from here.  Thoughts?

---

### Post by P4man on 2010-11-11
The log is rather clear. You have loaded nvidia 185 drivers which do not support your GPU. Uninstall them, then install the legacy drivers which do support your videocard.

If you installed the nvidia drivers through the "additional drivers" app, run

```
sudo apt-get remove nvidia*
```

If you installed them from nvidia website, you need to run the installer again with the --uninstall option.

---

### Post by Cyked on 2010-11-11
I ran apt-get to install the 185 drivers, which obviously didn't help, in an attempt to fix the issue.  I have changed the drivers since I setup the computer quite a while ago. Why did it crap out after the upgrade?

---

### Post by Cyked on 2010-11-11
Updating to 10.04 now after reinstalling the legacy driver.  

I booted twice to desktop and had an apparent kernel panic???  Computer froze with the caps lock and scroll lock blinking on keyboard.

Seemed to be running ok, so I decided to do the upgrade.

---

### Post by P4man on 2010-11-11
check your log again now that you (may) have the correct drivers. Or try removing the legacy drivers as well, see if your machine works okay with nouveau drivers. Your problem might be totally unrelated to the nvidia drivers and installing 185 might have put us on the wrong track.

---

### Post by Cyked on 2010-11-11
Apparently I had no drivers, according the logs anyway.

---

### Post by P4man on 2010-11-11
rename /etc/X11/xorg.conf to something else (like xorg.backup). It may still contain references to the nvidia driver. THe kernel has nouveau drivers built-in and doesnt require a xorg.conf.

---

### Post by gradinaruvasile on 2010-11-11
>  [COLOR="Red"]The NVIDIA GeForce4 MX 440 with AGP8X GPU installed in this system is supported through the NVIDIA 96.43.xx Legacy drivers[/COLOR]. Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more information. 
The 185.18.36 NVIDIA driver will ignore this GPU. 

Quite simple 
- you have a GeForce4 MX 440 card that is supported by the driver 96.43.xx.
- you have 185.18.36 version driver installed.

Solution: remove the current driver and install the 96.43.xx series driver. Make sure that nouveau is disabled (it should be disabled automatically).
And next time check with the nvidia website ([http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)) before installing drivers.

---

### Post by Cyked on 2010-11-11
So why was the legacy driver wiped in the first place?

---

### Post by gradinaruvasile on 2010-11-11
Beats me, probably some scripting error in the upgraded packages.
I always use the driver from nvidia directly and works perfectly fine (you have to reinstall on major kernel upgrades, but since you anyway have to reboot, its not a big thing).

---

### Post by P4man on 2010-11-11
I think proprietary drivers are always uninstalled upon an upgrade. But like I said, if you had a kernel panic without proprietary drivers, your issue might have been something completely else (though installing the wrong drivers obviously didnt help).

---

### Post by gradinaruvasile on 2010-11-11
Make sure that you disabled the nouveau driver:

In a terminal:

sudo gedit /etc/modprobe.d/blacklist.conf

or in text mode:

sudo nano /etc/modprobe.d/blacklist.conf

and append to the end (if not already there):

blacklist nouveau

save the file and reboot ("sudo reboot" in text mode).

Then boot into recovery mode and install the drivers in text more and reboot.

---

### Post by Cyked on 2010-11-11
> **gradinaruvasile said:**
> Make sure that you disabled the nouveau driver:

In a terminal:

sudo gedit /etc/modprobe.d/blacklist.conf

or in text mode:

sudo nano /etc/modprobe.d/blacklist.conf

and append to the end (if not already there):

blacklist nouveau

save the file and reboot ("sudo reboot" in text mode).

Then boot into recovery mode and install the drivers in text more and reboot.

Added the blacklist.  I'll reboot when I get home and can watch it.

---

### Post by P4man on 2010-11-11
didnt you uninstall the nvidia legacy driver earlier? You need either the nvidia driver or nouveau, if you removed nvidia and now blacklisted nouveau, you wont have anything to drive your display.

---

### Post by Cyked on 2010-11-11
Apparently not the case.  I thought I had as well, but still running the 96 driver it seems for the card with nouveau black listed.

Just before adding the nouveau blacklist entry i was still getting a boot issue wanting to boot with ubuntu in minimal graphics mode.  

Everything seems good now, no boot messages, logs look clean.

---

