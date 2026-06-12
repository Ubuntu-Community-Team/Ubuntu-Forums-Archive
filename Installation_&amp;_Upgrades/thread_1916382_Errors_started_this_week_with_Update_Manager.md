---
title: "Errors started this week with Update Manager"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by DMustaine on 2012-01-27
Just this past week I did like 20 some updates, then the next day Update Manager threw an error. Specifically it is this:

W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I've been using this install for over a year now, and have never used a CD to install anything. Notice in the error it shows 11.04, but when looking at System Info it says 11.10

I'm guessing that's where the root of the problem is, but I'll be danged if I can't find any reference to this type of error. Every search string I've thought of just shows how to upgrade from 11.04 to 11.10. I did that through Update Manager months ago, with no errors. I have been doing updates almost weekly since, until last week like I said.

Any suggestions would be very helpful.

---

### Post by 2F4U on 2012-01-28
Is it possible that the cdrom is configured as a repository? If yes, try to remove it from the repository list.

---

### Post by DMustaine on 2012-01-28
> **2F4U said:**
> Is it possible that the cdrom is configured as a repository? If yes, try to remove it from the repository list.

That was it! Well at least it says my system is up to date, and gave no errors looking for updates. We'll see in a week or so but I believe this was the issue.

Thanks a ton!

---

