---
title: "installing with raid, blank screen, what is it doing?"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by hotani on 2006-07-12
I set up RAID using the alternate install CD and following [this guide](http://users.piuha.net/martti/comp/ubuntu/raid.html). However, after committing the changes my screen is just sitting there - no status bar or anything, just empty blue. 

It has been going like that for almost an hour and I don't know if it is formatting or hung up. Should I just bag it and start over?

---

### Post by hotani on 2006-07-12
after about an hour of staring at a blank screen I decided it was toast and hard-booted.

Now both drives are hosed, the installer hangs during boot to tell me by outputting about 200 lines of I/O errors.

Currently I am staring at YET ANOTHER seemingly stuck screen that is scanning disks, and no doubt going through the same errors I just sat through.

And no, this isn't the first time I've dealt with hangs, freezes, trashed drives and multiple attempts to get Ubuntu installed on a system.

---

### Post by bender3000 on 2006-07-13
I had a success after I first did a **server installation** and afterwards when that was runnung I installed kubuntu-desktop

---

### Post by hotani on 2006-07-13
It looks like my problems were due to a HD failure. I am not sure if the installer had anything to do with it or not, but my second disk was unreadable (it was working before I started this process).

I re-did the array using my 250GB SATA drives and it worked. My experience with installing Ubuntu has been that if you can get past the partition editor you're golden. I'm now up and running, and will see if I can do anything with that disk or if it is really toast.

---

