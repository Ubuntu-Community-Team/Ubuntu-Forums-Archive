---
title: "vesafb issue after cleanup and can't boot past login screen"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by twistmypix on 2013-03-26
I've been searching for an answer for a couple days and if this has been  covered, please forgive me and please point me in the right direction.

The  other night, I was doing cleanup before imaging my partition, as I  usually do with bleachbit, janitor, and removing a couple cache  directories. This time, the only thing I changed was I included  "localizations" in bleachbit. My system seemed to lose every graphical  quality and I rebooted. Upon rebooting, I get the following error I've  seen documented abundantly: "FAIL: Error inserting vesafb  (/location/vesafb.ko) No such device". I had this before and gave up,  ultimately restoring from a previous clone zilla image. This time,  unfortunately, I can't because I have a plethora of data not backed up  that I need access to.

I've seen plenty of posts on this and all  the recommendations don't work. Upon boot, it no longer boots directly  into the OS, rather takes me to a login window, it attempts to login  after so many seconds, I get the error and a black screen, it takes me  back to the login window, and repeats.

I have the boot menu  hidden with startup manager and need to get to it or a command line to  repair, recover, etc. I've tried all recommendations I've seen of  depressing "shift", "esc", and even someone mentioning "alt+ctrl+f1".  The latter didn't seem to do anything while trying during startup.  However, when I depress "shift", I see "Grub loading." and nothing  after. It attempts to go back to the login screen and it's cyclical  repetition of annoyance.

(As  an update, I've gotten to the live cd and updated grub.  I now have a  boot menu if I hold shift down but that's it - same errors, same  everything...  Any ideas?)

Any help is greatly appreciated! Thank you!

---

