---
title: "Question about installation"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by inhumangeek on 2011-11-21
Not really a problem, more of a question so that I can be prepared. Currently on Ubuntu 11.04.

I currently have two main partitions on my HDD: i) system and ii) user data. System is (obviously) mounted at /, and the data is mounted at /home. These were created when I first built the computer. 

So, the question is, if wanted to perform a clean re-installation of Ubuntu, and I wanted to use the same partitions: mounting the first partition at /  (and formatting it), and mounting the second partition at /home, and NOT formatting it. I want to keep *all* the same data. 

Is it a simple case of going through the install process, choosing the correct partitions, mounting them in the right place? Can I be sure that data is not going to be wiped? 

And, if it does install OK, am I safe to have the same usernames? I assume it might be best to rename the (two) users folders before I install, to make sure there's no cross-contamination of settings, etc.

Any thoughts much appreciated.

Thanks.

---

### Post by Basher101 on 2011-11-21
as far as i know, having your /home on another partition will not wipe it on a reinstall. i have no experience on this tho, as i keep my whole install on one partition and just back that data up..

---

### Post by tartalo on 2011-11-21
All your assumptions are correct.

If you change usernames I guess that you will have to regain ownership of the files with chown

Another option, if you want a clean installation, is to move the hidden files to a folder, something like "mv .* oldpreferences" and recover only what you want after the installation.

Anyway, I'm not aware of any problem you could have if you just left everything there and used the same username, I've done it before.

---

### Post by inhumangeek on 2011-11-21
Thanks both. I'll give it a go.

All my important files are backed up online so I won't lose anything; it would just be a bit of a pain to restore them unless I really had to.

---

