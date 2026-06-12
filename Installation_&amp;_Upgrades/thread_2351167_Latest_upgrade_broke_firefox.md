---
title: "Latest upgrade broke firefox"
date: 2017-01-31
forum: Installation &amp; Upgrades
---

### Post by PaulBx on 2017-01-31
Linux len780 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
I'm on 16.04 Lubuntu...

Just upgraded from 4.4.0-57 using software updater; now firefox won't work. It opens the window and the tabs are set up properly, and it starts loading a website, but runs out of steam in the middle so I never get any page displayed.

I looked in dpkg.log at the firefox entries, saw nothing suspicious there.

I happen to have seamonkey also, and that works. It is what I am using to post here.

My other applications seem OK so far.

In kern.log I see a lot of these entries:
```
Jan 31 15:50:30 len780 kernel: [   53.864741] audit: type=1400 audit(1485906630.001:67): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/proc/4333/net/arp" pid=4339 comm=4C696E6B204D6F6E69746F72 requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

A couple days earlier they looked like this:
```
Jan 29 22:47:26 len780 kernel: [32920.089697] audit: type=1400 audit(1485758846.749:363): apparmor="ALLOWED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/proc/4441/net/arp" pid=4447 comm=4C696E6B204D6F6E69746F72 requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

Don't know how significant that is.

---

### Post by PaulBx on 2017-01-31
Never mind, it started working again.

---

