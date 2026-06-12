---
title: "Daily Build cd karmic differs from repo's"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by popeye on 2009-08-11
I tried to make a daily-live cd with rsync and it seems to be ok. [HTML]https://help.ubuntu.com/community/RsyncCdImage[/HTML]The md5sum is the same as on the site.[HTML]http://cdimage.ubuntu.com/cdimage/daily-live/current/[/HTML] I have burnt the iso on cd an added it to updatemanager. I have done a fresh install of the beta 3 iso. Now when updating via updatemanager it wants to download 250 mb of updates from the repos, but according to me all of that should be on the daily-cd as well. Seems strange to me, anyone any ideas?

---

### Post by b3n87 on 2009-08-11
There have probably been a load of updates since the last daily-cd ISO was made.

Correct me if im wrong but development is happening pretty much 24/7 because people all round the world are working, at different times. So no doubt there will be even more updates to install after you have finished reading this message :-p

---

### Post by popeye on 2009-08-11
Thanks, i was under the impression the daily build was reflecting the repo's at the moment, meaning that could make a difference every moment of the day as well.

---

### Post by psyke83 on 2009-08-11
> **popeye said:**
> Thanks, i was under the impression the daily build was reflecting the repo's at the moment, meaning that could make a difference every moment of the day as well.

If the daily-cd were to change constantly each day, how would anyone manage to download the ISO without it getting removed and replaced during the download process?

---

### Post by tekstr1der on 2009-08-11
That's too funny. The keyword being "daily" kind of hints at how often the image is built. Mozilla's build machines pump out hourly builds, but that's just a 7mb browser, not an entire OS. It is going to be a while before we are seeing "momentary" builds, I believe.

---

### Post by arky on 2009-08-11
The current is just a symbolic link that gets updated every day.

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

---

### Post by psyke83 on 2009-08-11
> **popeye said:**
> I tried to make a daily-live cd with rsync and it seems to be ok. [HTML]https://help.ubuntu.com/community/RsyncCdImage[/HTML]The md5sum is the same as on the site.[HTML]http://cdimage.ubuntu.com/cdimage/daily-live/current/[/HTML] I have burnt the iso on cd an added it to updatemanager. I have done a fresh install of the beta 3 iso. Now when updating via updatemanager it wants to download 250 mb of updates from the repos, but according to me all of that should be on the daily-cd as well. Seems strange to me, anyone any ideas?

I just re-read your post and realized what you were really asking.

The daily**-live** CD does not contain .deb packages that can be used as an apt-cdrom source - you must use the [daily]("http://cdimage.ubuntu.com/daily/") (equivalent to alternate) CD instead.

---

