---
title: "After partitioning NTFS, unable to mount it"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by heml0ck on 2012-12-23
Hey everyone,

Today my plan was to shrink a partition in my hdd so that after moving vital data out I could wipe it and then move it back the way it was. This is an NTFS partition used in win7, but since I couldn't do this while windows was running (despite the system/data partitions being seperate) I used the Gparted in Ubuntu 12.04 livecd.


This is what it looks like after it was done (I shrinked sda2 and created sda4, taking all the free space in sda2)

[IMG]http://i.imgur.com/MwSjT.png[/IMG]

As you can see, there now appears a warning next to sda2 ([the text of which is here.]("http://paste.ubuntu.com/1459937/")) and I'm unable to mount it. I should also mention that while in windows, this partition couldn't be shrinked more than ~10GB, the reason for which I couldn't comprehend. I checked whether there was any paging file located in this drive but there wasn't so I'm at a loss as to what's preventing it. 

I realize this isn't an ubuntu question per se, but partitioning & dualboot configs not being my areas of expertise; I decided to ask anyway before screwing up even further. Please tell me the data in sda2 isn't completely unrecoverable... ](*,)Any input as to what my next move should be from the community is appreciated, thanks.

---

### Post by darkod on 2012-12-23
That warning usually only means you need to run chkdsk on the partition in windows. Linux will refuse to mount it as long as there are errors on it. Don't try to mount it right now.

Boot into windows and run chkdsk /r on it. For example, if the letter of the partition is D: run something like:
chkdsk /r D:

That should repair any errors. Windows usually needs chkdsk after resizing ntfs partitions, especially with third party tools (or Gparted).

---

