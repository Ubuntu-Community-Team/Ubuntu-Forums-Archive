---
title: "intall of latest build via usb fails"
date: 2016-11-24
forum: Installation &amp; Upgrades
---

### Post by wozzman on 2016-11-24
Im new to ubuntu and I am tryin to install to a brand new internal laptop drive via usb..did the rufus and the latest build of ubuntu and it gets part way and an error comes up says bad dvd or internal drive,,its a new drive..i ran dignostic tests from bios and it says all is cool...any ideas?:confused:

---

### Post by ubfan1 on 2016-11-24
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media or
hardware problems.

---

### Post by wozzman on 2016-11-24
I did the verify integrity and that reported a error in 1 file

---

### Post by ubfan1 on 2016-11-24
If the error was in the ISO, download it again, and recheck it.  Torrents have additional checking which might work better.  I've used zsync (but not the Windows version) to update a beta ISO to the final release, so I'd guess that might be the fastest way to fix your ISO with a problem -- it should just download the bad part.

---

### Post by wozzman on 2016-11-25
Thank you very much for your help,,,downloaded new file and worked first time!!

---

### Post by ubfan1 on 2016-11-25
You're welcome.  Under the "thread tools" dropdown at the top of the thread, you may select "solved" to indicate that  in the title.

---

