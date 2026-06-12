---
title: "Gnome related system freeze ?"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by dbyrne on 2008-01-21
I've been running Gutsy for a couple of months, with regular system freezes about every 24-36 hours. I can't find any cores or log entries relating to the problem, but I noticed that if I didn't start Gnome after rebooting, the system stays up fine. Right now I haven't started Gnome since last reboot, and it's been up nearly nine days without a hitch.

I can't really think where to start troubleshooting this as it takes a long time to happen. I set up a cron job to output a "ps -aefl" to a log file, then a logrotate after reboot to ensure the logs doesn't get overwritten so that I could look to see if anything obvious was running or using up huge resource. However there's nothing particularly abnormal running in the 60 seconds before the system crashes according to the output.

Any ideas ?

---

### Post by erginemr on 2008-01-21
Hello,

For out of curiosity, which environment have you been working on if not running Gnome, another DE (such as Fluxbox, IceWM, etc.) or are you using the text mode only?

Secondly, does the freeze happen when Compiz Fusion is enabled? Does it happen when you disable the desktop effects?

And finally, what are your system specs?

---

### Post by dbyrne on 2008-01-21
Hi,

I'm using text mode only, via putty. I don't think I'm using Compiz Fusion unless it's enabled by default, and although I did switch on desktop effects under Feisty before upgrading (Feisty used to freeze too), I believe I've switched them off, at least I unticked the "Desktop Effects" tickbox. I'll re-check and google Compiz though - are these problematic ?

My system is quite old: Tyan Tiger 100 motherboard with dual Slot-1 Pentium III 500MHz CPUs, 1Gb RAM, 2xSeagate 300Gb Barracuda (RAID-1), 48x CD-RW, floppy. Runs great other than this freeze problem though, much better under Ubuntu than under anything else it's run: Win95, Win98, Win2k. Never froze under Windows though ...

---

### Post by erginemr on 2008-01-21
Not that they are problematic... maybe yes, they are problematic for quite a few people on the forums. But the fact that text mode runs well and graphical desktop stalls brings the graphics issues to mind in the first place.

Other than that, I am clueless. Hope you will unravel this mystery soon.

---

### Post by erginemr on 2008-01-21
On a second thought, if you have upgraded from Feisty, maybe the upgrade process has inherited this bug, config problem, or whatever into Gutsy. So, I suggest you to back up your files and configuration, salvage what you can and do a clean install of Gutsy.

---

