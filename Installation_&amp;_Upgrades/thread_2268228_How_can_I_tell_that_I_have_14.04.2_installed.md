---
title: "How can I tell that I have 14.04.2 installed?"
date: 2015-03-07
forum: Installation &amp; Upgrades
---

### Post by tom-bellas3rd on 2015-03-07
Hi all, just downloaded Ubuntu 14.0.4.2 from the official website. Installed without a hitch and updated to current. When I enter System Settings / Details to see what version it is, it just states 14.04. 

When I do a uname -a it lists:

Linux tfb 3.16.0-31-generic #41~14.04.1-Ubuntu SMP Wed Feb 11 19:30:43 UTC 2015 i686 i686 i686 GNU/Linux

Looking at above, it shows 14.04.1 instead of 2. I see the kernel has been updated but the version number seems wrong. Is this common? How can I tell besides the upgraded kernel that 14.04.2 is installed?


Many thanks!

-Tom

---

### Post by TheFu on 2015-03-07
more /etc/lsb-release

---

### Post by tom-bellas3rd on 2015-03-07
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"


Yay, thanks for that!  :)

---

### Post by Bucky Ball on 2015-03-07
Good news. Please mark the thread as solved (second link in my signature). ;)

---

