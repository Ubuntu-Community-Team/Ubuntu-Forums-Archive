---
title: "dist-upgrade to edgy without preserving config?"
date: 2006-10-06
forum: Installation &amp; Upgrades
---

### Post by userid on 2006-10-06
Dear All,

I am considering upgrading to Edgy Eft beta, and am wondering if it was possible to reset some of the configuration details as though it were a fresh install.

I have upgraded from Breezy through Dapper Beta and I have always had the old icons preserved. I'm also running an idiotic sound config I "deployed" in the early days (Breezy) and which I have never managed to  fix completely. My system is thus still in the "how do you get sound on linux? - turn on the radio"  age of affairs (one sound at a time, skype temperamental etc) ](*,) 

When upgrading, is there a way of ensuring that

[LIST]
[*]*certain* package configuration details are installed from scratch, e.g. sounds system?

[*]the artwork (icons, gnome etc) is updated to edgy specifications?

[*]XGL/Xorg setup parameters are changed?
[/LIST]

Thanks in advance for any responses.

Pete

---

### Post by Kateikyoushi on 2006-10-06
Then wouldn't it be the best solution to make a fresh edgy install ?

---

### Post by userid on 2006-10-06
Yes except that I'd have to pull all my gigs of data somewhere wouldn't I.. 

I am certainly aware that this is a convenience measure ;) 

It would be easiest if I could reconfigure existing packages to default settings *as though* they were being newly installed.

Any ideas?

---

### Post by orb9220 on 2006-10-06
Well when I did a fresh install of edgy all my /home was still there and had minimal effort. 
All my gnome panels,apps,etc... pretty much worked.

But I had a separate /home partition which is a great way to keep everything.

When ubuuntu is borked it sometimes is the only way is to do a clean install.

What I have seen on the forums trying to upgrade with /home on / partition seems more problematic.

---

### Post by userid on 2006-10-07
Sigh.. redoing partitioning and fresh install way forward perhaps..

---

### Post by Kateikyoushi on 2006-10-07
This time make a separate /home partition, then this won't be a problem during the next upgrade.

---

### Post by ssam on 2006-10-07
lots of settings are stored in you home directory

they are mostly in hidden files (file names start with a "."). you can do view -> hidden in nautilus.

could try making a new user account, and seeing what settings are reset in the new account.

---

### Post by userid on 2006-10-24
> **ssam said:**
> lots of settings are stored in you home directory

they are mostly in hidden files (file names start with a "."). you can do view -> hidden in nautilus.

could try making a new user account, and seeing what settings are reset in the new account.

I am aware of this. I think these are the user settings however, the sound system is part of the X config.

---

### Post by userid on 2006-10-24
Could I not remove --purge alsa, esd etc and then reinstall with fresh config?

---

