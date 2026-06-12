---
title: "Upgrade Question - Will I retain my settings?"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by NuxIT on 2012-05-01
Hi, I'm about to pull the trigger on this update and go from 11.10 to 12.04. Last time I did an upgrade from one Dist to the next it went smooth and retained my settings. I'm hoping this will be the same. This is on my old school PIII 600 Machine so I won't be messing with any Fancy GUI's. I just want it to retain the xfce desktop like it did on the last update. Do you think it will be the same if I update to this distribution? Thanks

---

### Post by jerrrys on 2012-05-01
I vote yes, but mileage may vary.  Done two release upgrades with out a hitch.  But your computer specks; im surprised that 11.10 even runs on that.

Think I would use [clonezilla]("http://clonezilla.org/") and clone your HDD incase you need to revert back.

---

### Post by NuxIT on 2012-05-02
> **jerrrys said:**
> I vote yes, but mileage may vary.  Done two release upgrades with out a hitch.  But your computer specks; im surprised that 11.10 even runs on that.

Think I would use [clonezilla]("http://clonezilla.org/") and clone your HDD incase you need to revert back.

I know. LOL. The specs call for Pentium 4, 1GHz Minimum memory : 384 MB for Ubuntu Desktop. I have just enough memory and it actually runs good on the piii 600 processor! 

I think I'm going to go ahead and pull the trigger (fingers crossed). Next, I'm trying to get it loaded on my P4 2.6c with 1GIG memory to check out Gnome 3 desktop. I can't get the boot CD to work right now on that system. Hope my Piii Update goes well! I remember the one thing that it doesn't like running during upgrade is xscreensaver! Not sure why. ```
sudo kill 1474 (xscreensaver)
``` :popcorn:

---

### Post by NuxIT on 2012-05-02
Upgrade successfully completed! (again) 

Notes on install: I click upgrade within gui!

Total files downloaded from what I noticed 1,747 files. Total time for upgrade was about 2 1/2 hrs.

disk space usage was @ 50% before upgrade. 
disk Space after: 51% ! Only 1% change!

This was probably because it cleaned up a bunch of files I choosed to removed on cleanup. 

On first bootup I FREAKED out AT first because when I tried to login it said: 
failed to load gnome and went back to login. Don't remember this from previous upgrade.

I needed to choose xfce option in a menu the was kind of hidden(whew)

Everything remains in check!
Printing,remote ssh config's, host files,firewall, google earth still works,dual boot,etc!

Went from:
styles@brits:~$ uname -a
Linux brits 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux

to:
styles@brits:/etc$ uname -a
Linux brits 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux
Solid! Gotta love xfce ubuntu for older systems! Seems to be running nice so far!

:guitar:

---

### Post by NuxIT on 2012-05-03
I take it back. Ran into a slight snag. My remote desktop doesn't work. I had a VNC over SSH setup and when I launch mstsc to connect to the desktop I get that same error. "failed to load gnome". Need to try and figure this snag out since this is one of the main uses for this box. I also have some sort of crash report on boot. Need to figure a few things out since this didn't happen on my last update.

---

