---
title: "Distribution Upgrade - what?"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by britseye on 2010-01-15
Can someone explain the difference between a 'distribution upgrade' and regular updates for security fixes etc.

I just upgraded from 9.04 to 9.10, and expected after the trauma of that exercise - X not working & so on - to have a pretty clean and stable system.

Does 'distribution upgrade' mean 'we have a 6 month deadline we like to stick to, but we weren't really ready', or does it mean that my download of 9.10-alternate had missing stuff even though it had the correct checksum?

---

### Post by fancypiper on 2010-01-15
With regular updates, you would still be running Ubuntu 9.04.

A distribution upgrade takes you to the next release, Ubuntu 9.10.

There were some pretty serious changes between these two, but my upgrade went smoothly, but after reading up a bit, I decided to "clean up" my system with a fresh install, choosing not to format my /home and data partitions.

If the md5sum checked OK, the downloaded ISO should be correct.

---

### Post by britseye on 2010-01-15
> **fancypiper said:**
> With regular updates, you would still be running Ubuntu 9.04.

A distribution upgrade takes you to the next release, Ubuntu 9.10.

There were some pretty serious changes between these two, but my upgrade went smoothly, but after reading up a bit, I decided to "clean up" my system with a fresh install, choosing not to format my /home and data partitions.

If the md5sum checked OK, the downloaded ISO should be correct.
But I installed 9.10, and now immediately after I did so it is saying it needs to download another 250 or so file.

---

### Post by slakkie on 2010-01-15
> **britseye said:**
> But I installed 9.10, and now immediately after I did so it is saying it needs to download another 250 or so file.

Yes, perfectly possible. Changes that were made after the final freeze have been postponed and as soon as the release is out, they will put these changes in -updates/-security. So when you upgrade (without network access), you will have to upgrade some packages depending on how much you installed. 

If you want to avoid this: 
* Minimal install CD (fetches from online repo's)
* Network upgrade (fetches from online repo's)
* Alternate CD + network (so it only downloads the packages which are updated on the repo's but not on the CD).

---

### Post by Forbees on 2010-01-15
ubuntu is constantly going under updates

even though 9.10 is still new, we have millions of users finding and reporting bugs or security leaks etc. which means we need to start putting out updates to fix them and better enhance the ubuntu experiance :)

main diff i see between a distro upgrade and a normal update is that a distro upgrade will have a newer kernel, probably a newer GUI, sometimes it comes with a newer GRUB, and it has new favorite softwares to default to

---

### Post by britseye on 2010-01-15
> **slakkie said:**
> Yes, perfectly possible. Changes that were made after the final freeze have been postponed and as soon as the release is out, they will put these changes in -updates/-security. So when you upgrade (without network access), you will have to upgrade some packages depending on how much you installed. 

If you want to avoid this: 
* Minimal install CD (fetches from online repo's)
* Network upgrade (fetches from online repo's)
* Alternate CD + network (so it only downloads the packages which are updated on the repo's but not on the CD).
It would be a nice enhancement then to allow the user to apply updates incrementally. My network connection sucks, and if there's a big download going on the machine is virtually useless, so if I could bite it off in chunks . . .

---

### Post by slakkie on 2010-01-15
> **britseye said:**
> It would be a nice enhancement then to allow the user to apply updates incrementally. My network connection sucks, and if there's a big download going on the machine is virtually useless, so if I could bite it off in chunks . . .

Then use the alternate CD for upgrading your release, with the network option (default on).

---

