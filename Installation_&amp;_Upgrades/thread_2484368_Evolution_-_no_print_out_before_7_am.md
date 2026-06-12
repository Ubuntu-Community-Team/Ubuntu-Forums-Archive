---
title: "Evolution - no print out before 7 am"
date: 2023-02-24
forum: Installation &amp; Upgrades
---

### Post by decflagaz on 2023-02-24
I am using Evolution 3.44.4 on Ubuntu 24.04.2.  If you print out a calendar in Evolution, items listed prior to 7AM do not show.  Has anyone else experience this? More important - fixed it.

---

### Post by TheFu on 2023-02-26
Calendar programs often has a "workday hours" setting.  I haven't looked at Evolution in over a decade, but I suspect that's it. It will be buried in the settings somewhere.
[https://help.gnome.org/users/evolution/stable/calendar-layout-views.html.en](https://help.gnome.org/users/evolution/stable/calendar-layout-views.html.en) and [https://help.gnome.org/users/evolution/stable/calendar-layout.html.en](https://help.gnome.org/users/evolution/stable/calendar-layout.html.en) is what google found when I searched. Not sure if either apply to your situation.

---

### Post by decflagaz on 2023-02-26
Thanks for your reply and links.  Under Preference - Calander & Task you can set your work hours and day.  But changes to these items has no effect on the print out.  What is really change is that the problem does not exist if you use Lubuntu 22.04.

---

### Post by TheFu on 2023-02-26
> **decflagaz said:**
> Thanks for your reply and links.  Under Preference - Calander & Task you can set your work hours and day.  But changes to these items has no effect on the print out.  What is really change is that the problem does not exist if you use Lubuntu 22.04.

If 1 version works and the other doesn't, I'd check
* Evolution version differences
* Config difference for evolution on each system.  

I'd look for config files in ~/.config/evolution/ on both systems.  Might try moving the non-working one to a temporary name and copying over the working one to the expected location, then run the program. See if that makes it work as you'd like.

Any chance that evolution is a snap package for 1 install and a debian/APT package on the other? Sometimes there are odd things broken with snap packages that don't make sense.

---

### Post by decflagaz on 2023-02-26
I did absolutely nothing and the problem has resolved itself:  can not explain it.:o

---

### Post by TheFu on 2023-02-26
> **decflagaz said:**
> I did absolutely nothing and the problem has resolved itself:  can not explain it.:o

That's scary.  

Computers don't change the output from local stuff magically.  Now, if the calendar entries were pulled over the network, perhaps tied to a network ical or calDAV setup, then it could have been just a network hiccup that was resolved later.

But if everything is local, any chance the disk is corrupted?  I'd run an **fsck** on the file system used by /home and I'd **reinstall** evolution to see if there was some bad bits as part of any logical corruption.  If all those come back clean, I'd start watching the SMART data and ensure I had backups for anything I cannot lose - at least weekly, perhaps daily or hourly using LVM snapshots.  Backup tools like Back-In-Time do hourly change-only data copies using hardlinks. As the copy becomes older, more and more of the copies are removed, so that storage used doesn't go crazy.  Having hourly copies for the last 2 days (rolling period) can be nice.  After a few weeks, only the weekly copies remain and after a few months, only the monthly copies remain. Because hardlinks are used, only changed files are actually copied, which means that if nothing actually changes, very little real storage is used for a complete copy. Basically, just inode storage, which was already pre-allocated during the file system format process. It is fairly efficient and easy to understand.  If you don't know about hard links:  [https://en.wikipedia.org/wiki/Hard_link](https://en.wikipedia.org/wiki/Hard_link) explains in simple concepts.  This is nothing new. Hardlinks for backups have been around and used longer than I've been using Unix .... which is about 30 yrs.

---

