---
title: "Fresh Install 14.04 Trusty Beta 2"
date: 2014-04-09
forum: Installation &amp; Upgrades
---

### Post by brosskgm on 2014-04-09
I just did a complete 64Bit fresh install to Seagate Pipeline HD 2 500Gb SATA harddrive.

Intell 2.5Ghrtz Dual Core 4Gb Ram.

Install went flawless. When I boot the system, it gives the following error at every boot up.

error : malformed file
Press any key to continue.......

I could not locate an error log under /var/log .

Thanks
Bob

---

### Post by grahammechanical on 2014-04-09
Is there any indication as to the point in the loading process this error appears? We still need to do updates, perhaps on a daily basis, to trusty tahr. This problem might be fixed by an update.

Regards.

---

### Post by brosskgm on 2014-04-09
The screen is blank, No boot information or process, but the error shows just as the border around the screen edge is shown.

> **grahammechanical said:**
> Is there any indication as to the point in the loading process this error appears? We still need to do updates, perhaps on a daily basis, to trusty tahr. This problem might be fixed by an update.

Regards.

---

### Post by bapoumba on 2014-04-09
I got that message a couple days ago. Pressing a key got me booted up, I ran update/upgrade, rebooted and never saw it again.
I just thought of a hiccup as it booted up, after thinking of a grub problem.

---

### Post by brosskgm on 2014-04-09
Thanks for your replies.

Same here for pressing key to boot. I'll try the update/upgrade in about 15/20 minutes. I wasn't sure
that would have been needed since I just downloaded the iso this morning.

Thanks
Bob


> **bapoumba said:**
> I got that message a couple days ago. Pressing a key got me booted up, I ran update/upgrade, rebooted and never saw it again.
I just thought of a hiccup as it booted up, after thinking of a grub problem.

---

### Post by brosskgm on 2014-04-09
I'm running the update now. 95+ megs. But I did notice an update error that has me concerned.

GDKPixBuf * WARRNING * Can not load pixbuf loader
Likely means your installation is broken.



> **bapoumba said:**
> I got that message a couple days ago. Pressing a key got me booted up, I ran update/upgrade, rebooted and never saw it again.
I just thought of a hiccup as it booted up, after thinking of a grub problem.

---

### Post by brosskgm on 2014-04-09
Update finished, now I have a additional happening.

Now it gives me the boot screen to select *Ubuntu or other advanced boot options after every reboot/cold boot, then after it starts *Ubuntu I still get the error : malformed file press any key to continue.

It's not a big deal. I'm not running anything else on the hard drive, just this beta 2 so I could see how it's working. My working system has 12.04. I'll run an update over the weekend and see if it still does it and maybe even do a clean install.

Thanks
Bob

---

### Post by bapoumba on 2014-04-09
I searched for the error the other day, searched again today and did not find anything..

---

### Post by brosskgm on 2014-04-09
Could be one of those things since they only have AMD 64bit iso. I'm running intel.



> **bapoumba said:**
> I searched for the error the other day, searched again today and did not find anything..

---

### Post by bapoumba on 2014-04-09
Old Intel 1,6GHz, 1GB ram here, lubuntu 32-bits.

---

### Post by RickKnight on 2014-04-23
> **brosskgm said:**
> The screen is blank, No boot information or process, but the error shows just as the border around the screen edge is shown.

I have this same issue, but in my case it shows up before the border is drawn. I also lost the boot splash screen.

Rick

---

### Post by RickKnight on 2014-04-23
> **bapoumba said:**
> I got that message a couple days ago. Pressing a key got me booted up, I ran update/upgrade, rebooted and never saw it again.
I just thought of a hiccup as it booted up, after thinking of a grub problem.

I'll try this tonight. Thanks.

Rick

---

### Post by bapoumba on 2014-04-23
> **RickKnight said:**
> I'll try this tonight. Thanks.

Rick
For what it's worth, I choose the space bar..

---

