---
title: "Updates break HAL in hardy heron"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by MooneyDriver on 2008-01-21
I installed Hardy Heron on my dell 8100 laptop from the iso. It worked fine. I ran aptitude-update. After restarting, I get the error message "Failed to initalize HAL" when I sign in. Other users are apparently having this problem as well, see bug#25931. None of the proposed fixes on that page work. Other users are apparently having the same problem. The problem is probably underreported because the bug disables network adapters, among other things. Any ideas?

-Kyle

---

### Post by caryb on 2008-01-24
Mine is broken as well but my network is ok! but I have to connect in safe mode & run sudo startx to get a gui.


Cary

BTW I have added to the bug report

---

### Post by Rocket2DMn on 2008-01-24
That is part of the nature of being a Testing/Development user.  With this version you get updates that are not stable.
If this is not what you want, you should be using Ubuntu 7.10 - Gutsy Gibbon, this is the latest stable release of Ubuntu.  Hardy Heron is set for stable release in April, but until then, it's still considered unstable and therefore easily breakable.

---

### Post by MooneyDriver on 2008-01-28
> **Rocket2DMn said:**
> That is part of the nature of being a Testing/Development user.  With this version you get updates that are not stable.
If this is not what you want, you should be using Ubuntu 7.10 - Gutsy Gibbon, this is the latest stable release of Ubuntu.  Hardy Heron is set for stable release in April, but until then, it's still considered unstable and therefore easily breakable.

I am aware of the fact that I should expect problems with an alpha release.  I was hoping to increase the likelihood of a developer finding and fixing this bug.

-Kyle

---

