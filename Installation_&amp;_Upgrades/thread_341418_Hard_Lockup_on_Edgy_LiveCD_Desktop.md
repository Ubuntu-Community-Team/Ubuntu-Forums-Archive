---
title: "Hard Lockup on Edgy LiveCD Desktop"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by Gobboman123 on 2007-01-18
I've got a problem and I have no clue how to fix it.

I've had Ubuntu installed on this machine before and it worked amazingly well.  Anyhow for some reason it started completely locking up on me at the graphical login screen.  I've had it for a while so I thought, hey I'll just reinstall.  No biggie.  All my important files are on a different drive.

I wiped the drive that I have Linux on (I dual booting with Windows XP on its own drive) with GParted and then proceeded to boot up the Edgy LiveCD.  Everything seems to go fine until the point that I am able to see my mouse pointer.  I am not able to move my mouse at all.  Everything continues loading in the background.  After a couple of minutes I try moving my mouse, using the keyboard... trying some escape keys.  Everything is completely locked up.  I'm not sure what to do.

I tried booting DamnSmallLinux off a pen drive and it locks up too.  Actually it may have been using damnsmall that caused the problem in the first place (I don't know how) as the problems started right after using it the first time, earlier in the day.

---

### Post by john_spiral on 2007-01-18
Looks like you might have some type of hardware problem? 

is Windows booting fine?

---

### Post by Gobboman123 on 2007-01-18
After I fixmbr'd my Master Boot Record (because Grub wasn't loading) Windows is working perfectly.... sadly Windows working perfectly isn't saying much.  Anyhow, Windows is working like it always has.

---

### Post by john_spiral on 2007-01-18
Have you done a md5 sum check on the ubuntu CD? Could be your burner that's up the shoot?

---

### Post by Gobboman123 on 2007-01-18
It seemed like the CD check locked up at the end as well.  The drive itself is quite new, and I installed off this disc the first time.  I am halfway done downloading another iso though.

---

### Post by Gobboman123 on 2007-01-18
I'm getting the same error on the new iso I just downloaded.  I'm not sure what the problem is though, because Ubuntu was working on the same machine earlier in the day before I wiped it.  I have not installed anything new.  I know that the install is partially functioning.  I saw that the time-clock in the corner was still advancing each minute.

](*,)

---

### Post by Gobboman123 on 2007-01-20
I brought it up in another post, but I got it working.  I tried a gentoo livecd and it worked fine... had some other problem though, looked it up, tried that solution in Ubuntu... and everything worked out.

I added acpi=ht to boot and somehow that fixed things.  I don't really know how though as I was running the system fine before and then it stopped working all of a sudden (and I hadn't changed any hardware or anything).

---

