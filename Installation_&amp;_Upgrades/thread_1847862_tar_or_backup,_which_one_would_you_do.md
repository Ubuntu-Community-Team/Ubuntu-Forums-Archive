---
title: "tar or backup, which one would you do?"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by dcollier on 2011-09-21
Hello all, I set up and Ubuntu desktop between 1 and 2 years ago.  The customer called stating that she is no longer able to update "true bc of the old version"... So i am going to upgrade to the latest distro,  but my question is "is there a better way beside creating a tarball of the old home directory and extracting it to the new home directory or would a backup application work better than tar?  How would you do it?

---

### Post by Beacon11 on 2011-09-21
I would say it depends on how large the home directory is. You don't want a corrupted archive. Regardless of how you do it, when you reinstall I would recommend creating a home partition so you don't need to touch it for future reinstalls.

---

### Post by dcollier on 2011-09-22
So let me get a more clear understanding, if I had originally created a separate partition for home then all I would have needed to do was upgrade the root partition and leave the home partition alone?

---

### Post by haqking on 2011-09-22
> **dcollier said:**
> So let me get a more clear understanding, if I had originally created a separate partition for home then all I would have needed to do was upgrade the root partition and leave the home partition alone?

you could do that, thats why a lot of people have a seperate /home.  However /home also contains configuration data and so when upgrading there might be some minor issues.

I personally always make sure my backups are upto date, do a fresh install and copy personal data back

---

### Post by dcollier on 2011-09-22
Thanks for all the inputs!!!

---

### Post by Beacon11 on 2011-09-22
> **dcollier said:**
> So let me get a more clear understanding, if I had originally created a separate partition for home then all I would have needed to do was upgrade the root partition and leave the home partition alone?

Yes-- you can reinstall on the root partition while not touching the home partition.

> **haqking said:**
> However /home also contains configuration data and so when upgrading there might be some minor issues.

Agreed, which is why a lot of people choose to HAVE a separate home partition (keeping their configuration data). If this is an issue however, in my opinion it's simpler to delete all configuration data in the home directory than to back everything up. My biggest problem with the separate home partition is being stuck to a certain size. As soon as I limit the amount of space I have available, I tend to fill it up. So in my personal installs, I always only have root and swap.

---

