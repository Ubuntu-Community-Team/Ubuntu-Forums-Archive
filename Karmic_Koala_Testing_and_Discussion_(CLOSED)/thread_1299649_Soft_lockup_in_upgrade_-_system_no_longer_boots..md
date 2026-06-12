---
title: "Soft lockup in upgrade - system no longer boots."
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by merlyn on 2009-10-24
I've recently come back from a short holiday, (2 weeks), and decided to upgrade to the RC build of Karmic on my test drive.

During the update process the following error message preceded by a changing series of numbers appeared at one stage while the debs were being unpacked.

```
BUG: soft lockup - CPU#0 stuck for 61s
```

This repeated for four lines before I attempted a system reboot.

After a number of reboot attempts one of two things will happen.

1) system locks up when mounting partions due to "an entry in /etc/fstab cannot be mounted, or

2) screen goes blank (no text, nothing), and the back light goes on and off.

I've never seen this before, any ideas anyone.

I'm downloading the RC iso at the moment in case a fresh install is required.

The stability problems I've experienced with Karmic over the last month are disappointing to say the least, this will be the fourth fresh install.

And no it's not a Hardware issue, (I'm tired of hearing that), as Debian SID runs perfectly on the same system installed on my main hardrive.

And no it's not the Test Drive either, (I'm tired of hearing that also), it's a new drive, (one month old), bought for the purpose of doing test installs.

---

### Post by dino99 on 2009-10-24
hi,
everything fine here.
Try to clean cache first:
- sudo aptitude clean / autoclean
- sudo apt-get autoremove
- sudo aptitude install -f

then,
- sudo aptitude update
- sudo aptitude safe-upgrade

What are the logs saying ?
maybe reinstall the graphic driver.

---

### Post by merlyn on 2009-10-24
Hi, thanks for getting back to me.

Your advice would be useful but for one thing, as per my original post the system does not boot, i.e. no login, no command prompt.  :roll:

Perhaps in future I shall state the obvious, when making posts.

---

