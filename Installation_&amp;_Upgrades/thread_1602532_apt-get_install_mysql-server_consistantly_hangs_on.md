---
title: "apt-get install mysql-server consistantly hangs on 6% download"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by RockSolidAfrica on 2010-10-21
I have tried all kinds of ways to get apt-get to download mysql server but it keeps hanging on 6% of the download!
If it fails and I try again it hangs on downloading headers...

The only way I can get it going again (somehow) is by manually deleting the partially downloaded deb file in /var/cache/apt/archives/partial/
But then it just keeps hanging on 6% again.

I even keep trying different mirrors, same story
I have tried cleaning the cache with aptitude, same story
I tried a download mirror which uses ftp, same story

What am I doing wrong?
Does somebody understand this?

---

