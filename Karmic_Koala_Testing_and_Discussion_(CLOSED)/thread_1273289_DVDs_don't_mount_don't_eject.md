---
title: "DVDs don't mount don't eject"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by barisurum on 2009-09-23
I'm unable to mount or eject DVDs with alpha6. the eject button on the dvd drive's panel doesn't work too. CDs mount OK, read OK, eject OK. When I do:

> eject

it ejects only the cdrom drive.

edit: wait a minute, if I put a cd, use it and eject it, the eject button on the CDROM drive doesn't work too anymore, even if the drive is empty!

edit: SOLVED with latest brasero update

---

### Post by barisurum on 2009-09-23
anybody with the same problem?

---

### Post by VMC on 2009-09-23
Yes, just to let you know I have the same problem. I haven't investigated it yet.

---

### Post by steeleyuk on 2009-09-23
Same issue.

Pressing the button on the DVD drive doesn't eject but ejecting via Disk Mounter in GNOME does.

---

### Post by novafluxx on 2009-09-23
I'm willing to bet this has something to do with HAL depreciation

---

### Post by mc4man on 2009-09-23
It's been broken and fixed, broken and fixed again over the last couple of days and may break again.
Your best bet is to keep updating. (if the update manager doesn't show any updates click the blue 'check' button to make sure.

It's currently working on 2 systems here though this morning's updates temporally broke it again.

Best thing to do if it's not working is boot up with a data cd, dvd, or dvd movie in the drive(s). (vs removing a certain file that seems to be problematic

---

### Post by barisurum on 2009-09-23
I want to file a bug report of it but which package is it related to (udev, devicekit?) and how to debug? If anyone knows please do it or tell me how. Thanks.

---

### Post by blakamin on 2009-09-23
Yeap, broken here.

---

### Post by executorvs on 2009-09-23
Acer timelines have been having an issue like this one in jaunty as well. the bug for it is [https://bugs.launchpad.net/ubuntu/+bug/412527](https://bugs.launchpad.net/ubuntu/+bug/412527) check to see if any of the fixes work.

to get mine to work, once I've got a disc in, I need to suspend and resume to get it to mount.

---

### Post by mc4man on 2009-09-23
Here is the bug report, notice that it says fixed at end. There are some dups. I had filed a slightly different one that got marked as a dup though it specified all data cd's. dvd's and dvd_video.

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/430605](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/430605)

Anyway the fix lasted all of about 12 hrs., when a fix for running gksu nautilus broke it again.
This thread moved from gksu to automount
[http://ubuntuforums.org/showthread.php?t=1272189&page=2](http://ubuntuforums.org/showthread.php?t=1272189&page=2)

Anyway late yesterday a fairly large update fixed it yet again, and there has been even more updates today including hal, udev, gnome2 etc.

All is good here on 2 machines now, though there was some indication that there could be some hardware specific differences. (or breakages

I first d. check that your are truly up to date. As mentioned you can't 'trust' the update manager, use the check button. If updates then show up, apply, reopen the update manager and use the check button again, more may show up

---

### Post by barisurum on 2009-09-24
OK the status update after the latest upgrades:

CDs and DVDs mount and eject but only once. And after that I can't open the drive tray with the eject button on the drive panel. Added that to the bug report.

---

### Post by burntresistor on 2009-10-04
I'm having the same problem. I find running eject through terminal helps on some of them,but others that wont even work.

---

### Post by cornflake000 on 2009-10-04
add me to the list... no prob before... now the identical issue as stated.  I'll dig around and look for a fix...

---

### Post by barisurum on 2009-10-04
Problem persists in BETA, first dvd mounts and I watch the film but then the tray doesn't open

---

### Post by nanog on 2009-10-04
This fixes it for me when I am too impatient to wait:

```
sudo hal-disable-polling --device /dev/cdrom --enable
```

---

### Post by mc4man on 2009-10-04
A fix for both the locked drive and or failure to automount cd's, dvd's ect. should be forthcoming shortly

---

### Post by jperez on 2009-10-05
Thanks for the info.  I just barely started using the CD/DVD Burner on my laptop to test DVD playback that I saw others having.  Found the issue and fixed that but then came across the issue presented in this thread.

Testing is fun, ain't it? :lolflag:

Jesse~

---

### Post by mc4man on 2009-10-05
This is the most relevant bug report which now has a "fix released", so look for an update and see how it goes

[https://bugs.launchpad.net/ubuntu/karmic/+source/brasero/+bug/438065](https://bugs.launchpad.net/ubuntu/karmic/+source/brasero/+bug/438065)


Look for this updated version # in near future
brasero (2.28.1-0ubuntu1)

Edit: Works here for all media

---

### Post by executorvs on 2009-10-06
I wish this was the issue with the acer timelines, it seems to be getting fixed. but as you can't mount CD/DVDs in the timeline series(without terminal or booting with media in drive) this is likely not my bug. :-(

---

### Post by mc4man on 2009-10-06
@ executorvs
I can see you've searched some prior threads concerning timelines, why don't you edit in your model number  just in case something specific to it shows up

---

### Post by executorvs on 2009-10-06
> **mc4man said:**
> @ executorvs
I can see you've searched some prior threads concerning timelines, why don't you edit in your model number  just in case something specific to it shows up

may seem dumb but given the two hours of sleep I had last night(6-8ishAM) and the fact that it's already 2:30AM I'm not sure I follow. at current I'm subscribed to every 4810T/5810T/Acer Timeline thread/bug report I've found on launchpad and the forums and then a few others because they looked similar.

my eyes are feel like they're burning right now which means I should go to sleep soon... just need to finish paper.

---

### Post by mc4man on 2009-10-06
Was only asking because posts have come up occasionally for quite some time about acer timelines and they usually mention this model or that model and you didn't.
> at current I'm subscribed to every 4810T/5810T/Acer Timeline thread/bug report
You seem to be on top of it

---

### Post by barisurum on 2009-10-06
After the latest brasero udate the problem seems to be fixed, thanks to all who participated :)

---

### Post by Grimhound on 2009-10-06
I got the problem to pop back up when I tried to use Sound Juicer. In full glory.

---

### Post by terry_gardener on 2009-10-06
Grimhound

this sounds more like bug #397734 (the eject button on drive doesn't work when mounted)

when i play a dvd-video it mounts and plays ok now with this new libbrasero-media0 2.28.1. i cant eject using the drive button but can unmount/eject using nautilus, then drive button works again until i insert another dvd-video.

basically until bug #397734 is fixed (which fix has been commited for review but not released) you are going to get this problem where the drive button doesn't work until you unmount/eject the drive or logoff and back in.

hope this helps

---

