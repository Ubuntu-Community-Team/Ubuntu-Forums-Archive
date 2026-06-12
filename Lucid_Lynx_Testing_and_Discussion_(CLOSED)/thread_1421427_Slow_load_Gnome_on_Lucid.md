---
title: "Slow load Gnome on Lucid"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Yahoé on 2010-03-04
On a lucid clean install, and only for the past 3 to 4, this started to happen after installing recommended updates, the transition from GDM to the Gnome desktop is slow whenever it use to be instantaneous.

Any idea why?

Regards,

Alain-Olivier

---

### Post by spiderbatdad on 2010-03-04
lucid is currently in alpha the first beta release is due March 18. So asking for support or running Lucid and expecting it to behave like a release candidate isn't reasonable.
Instead, post your experiences or discussions in Lucid Lynx Testing:
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by Yahoé on 2010-03-05
Thank you for your answer [spiderbatdad]("http://ubuntuforums.org/member.php?u=55512"), I'm very aware of what an Alpha release is, I was just just curious of why this is happening, the first time in many releases in fact.

Regards

---

### Post by Yahoé on 2010-03-20
I have now done a fresh install of Lucid Beta 1 and no improvement on the transition from GDM to Desktop.

Yahoé

---

### Post by daas88 on 2010-03-20
I have the same problem, fast boot, but slow transition from gdm to gnome desktop =/ I hope this gets fixed soon!

---

### Post by Uncle Spellbinder on 2010-03-20
Lightning quick for me on 2 different computers.

---

### Post by jfernyhough on 2010-03-20
Try a ureadahead reprofiling: [http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

---

### Post by ruik on 2010-03-20
> **daas88 said:**
> I have the same problem, fast boot, but slow transition from gdm to gnome desktop =/ I hope this gets fixed soon!

I have this too, actually it's been like this since alpha 1. I did a reinstall few days ago but no change.

---

### Post by Yahoé on 2010-03-22
As advised I tried to reprofile to no avail. Going from from user login to Desktop still takes several seconds. Installed Lucid Beta 1 to a different computer, and I don't experience this on it.

Is ureadahead still used to accelerate from boot from login prompt to desktop load?

Regards

---

### Post by sfreed on 2010-03-29
> **Uncle Spellbinder said:**
> Lightning quick for me on 2 different computers.

I'm having the same problem.


 Could you do us a favor (if you haven't already) and create a new user (or delete all your .??* files) and see if this makes a difference to your "Lightning quick" login?

I first noticed the very slow login process after I blew away all my dot files (on purpose) after the Alpha 2 release. 

--
thanks
steve

---

### Post by sfreed on 2010-03-29
Could those of you who are having this problem please post the relevant section of your .xsession-errors file?  ...like the first 150 lines or so.

Thanks.

--
steve.

---

### Post by daas88 on 2010-03-30
I'm still experiencing this and I filed a bug in launchpad about that, please comment and click "this bug affects me"

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/551712](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/551712)

---

### Post by kansasnoob on 2010-03-30
> **daas88 said:**
> I'm still experiencing this and I filed a bug in launchpad about that, please comment and click "this bug affects me"

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/551712](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/551712)

Done ;)

Could you also list your hardware and attach your bootchart as I did?

---

### Post by sports fan Matt on 2010-03-30
With ya'll's bootcharts, just how slow are we talking?  This isn't affecting me per se, but would like to know in case it slows down.

---

### Post by JustRon on 2010-04-01
I don't know if it helps but my Gnome startup from GDM was much faster after I disabled the nonexistent floppy drive in the BIOS. Before that the Gnome loading seems to take a break for several seconds without any hard disk activity.

---

### Post by Winter Skies on 2010-04-07
> **JustRon said:**
> I don't know if it helps but my Gnome startup from GDM was much faster after I disabled the nonexistent floppy drive in the BIOS. Before that the Gnome loading seems to take a break for several seconds without any hard disk activity.

Yup disabling floppy drive fixes slow transition from gdm to gnome.

Thanks.

---

### Post by sfreed on 2010-04-07
Yup. It's the floppy drive. Who woulda guessed.

--
steve.

---

### Post by daas88 on 2010-04-07
On the BIOS you say? I'll reboot, check if it's enabled and post telling you my results.

Edit: Well it certainly starts a faster, the desktop loads in like 3 seconds in contrast to the 15~25sec before. But it's still like 20 seconds from grub to blue bars (supposed to be plymouth, I'm using nvidia drivers) and finally gdm.

---

### Post by psyke83 on 2010-04-07
> **Yahoé said:**
> On a lucid clean install, and only for the past 3 to 4, this started to happen after installing recommended updates, the transition from GDM to the Gnome desktop is slow whenever it use to be instantaneous.

Any idea why?

Regards,

Alain-Olivier

I see a very jerky transition from Plymouth to GDM when kernel modesetting is disabled (radeon driver), but it is smooth when kernel modesetting is enabled. Is that what you're seeing?

---

### Post by Tsu jan on 2010-04-11
It seems that I'm too late in this forum. I just wanted to say that since a few days ago, I got exactly the same problem in my Debian Squeeze too. It was after I upgraded some packages. A new package named "udisks" was installed and a floppy icon appeared on computer:///, although I have no floppy driver. I disabled the floppy in BIOS and the problem was fixed.

In my opinion, this new behavior in Debian and Ubuntu (and perhaps in the future versions of other distros) is logical, although confusing at first.

---

### Post by linusr on 2010-04-11
I have same issue in Dell Vostro 1500 after upgrade to Lucid from Karmic.

No floppy drive and no option in BIOS to disable it. Attached bootchart..

---

