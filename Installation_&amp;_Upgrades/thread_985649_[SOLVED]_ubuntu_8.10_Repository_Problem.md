---
title: "[SOLVED] ubuntu 8.10 Repository Problem"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by melenor on 2008-11-17
Okay, so i recently installed ubuntu 8.10 on my sister's computer (she loved 8.04) but after booting up i can't install updates or install any programs, every time i try to do something i recieve this error
```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.


```
The computer is connected to the internet, i enabled all restriceted repos, i did everything the same as my first install and that worked and almost everything just like the second time i installed it for someone. Thanks

---

### Post by inobe on 2008-11-17
the servers seem to be down if i'm not mistaken.

those links can be pasted into your browsers address bar

> Not Found

The requested URL /ubuntu/dists/intrepid/partner/i18n/Translation-en_US.bz2 was not found on this server.

edit: i refreshed and some of my sources have failed

---

### Post by melenor on 2008-11-17
I am not quite sure but when i restarted it worked again thank you everyone.

---

### Post by inobe on 2008-11-17
when ever that happens do

```
sudo apt-get update
```

in terminal then paste the results

---

