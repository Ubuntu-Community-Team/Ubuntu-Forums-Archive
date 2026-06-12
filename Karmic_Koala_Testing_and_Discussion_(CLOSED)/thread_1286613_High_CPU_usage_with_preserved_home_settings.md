---
title: "High CPU usage with preserved home settings"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lovinglinux on 2009-10-09
I have installed Karmic, keeping the home partition intact. It didn't work well, because something in my old settings where causing a high CPU usage, not detected by top. I have tried to pinpoint the culprit without success. Then I decided to create a new user and the problem didn't persist, so I did a fresh install, completely wiping my home settings files and the problem didn't appear this time.

I'm wondering what could cause this, since I have seen lots of similar issues in other forums not dealing with Karmic Beta release. Most of the time I have posted in such threads, the abnormal CPU usage in Jaunty was caused by vino-server, but some users weren't able to detect and solve the problem.

Any ideas?

---

### Post by airtower on 2009-10-27
I was having the same problem...I have had the same /home partition for years and I was experiencing heavy CPU usage after upgrading to 9.10. CPU loads in top did not sum up to the total CPU load reported (although I did not trying running top as root, if that would even make a difference).

removing vino fixed the problem for me.

---

