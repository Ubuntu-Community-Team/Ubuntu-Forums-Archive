---
title: "Update manager appears to be broken!"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by RedMartin on 2008-06-26
Ubuntu 8.04 - kernal 2.6.24-19

I've noticed over the last few days that my usual evening notification of updates has failed to appear.

However, when I manually start the update manager it tells me there are updates available.

Everything that should be checked is. I'm stumped.

Any ideas?

---

### Post by avtolle on 2008-06-26
Have you then been able to install the updates? How often do you have the update manager check for new updates? I'm trying to recall just where that is so you can look at the appropriate menu to check, and cannot right now.

EDIT: Look under System>>Administration>>Software Sources, updates tab, and see where it is set, e.g., daily, weekly, etc. Change to daily. Also, I've noticed on my system that sometimes it is an hour or two (usually shorter time) before first the gray cogwheel or whatever appears in the top panel, and then, if there are updates, it turns orange (or the orange arrow, signifying security updates) and I am able then to download them.

---

### Post by RedMartin on 2008-06-27
It is set to daily.

I found a thread in the archives (thanks Google) that mentions the same probem but in Hoary. The remedy is to reinstall update-notifier. I've done this and will post up if it works or doesn't

Interestingly, I've never noticed the normally orange arrow can be red. Critical updates I presume.

---

### Post by RedMartin on 2008-06-28
It works. Updates a plenty.

---

