---
title: "&quot;Intel Graphics update tool for linux OS&quot;  Failed to Update"
date: 2017-02-11
forum: Installation &amp; Upgrades
---

### Post by aruodg on 2017-02-11
Hi
installed **Intel Graphics update tool for linux OS** to install and update intel GPU driver.
However, each time i run this tool i got an error message, see the screenshots.
because I am still unable to get full HD resolution.
:confused:

---

### Post by howefield on 2017-02-12
For your graphic driver issue try this post..[https://ubuntuforums.org/showthread.php?t=2342137&p=13565767&viewfull=1#post13565767](https://ubuntuforums.org/showthread.php?t=2342137&p=13565767&viewfull=1#post13565767)

For the ffmpeg error, there is no yakkety release for that repository so you are basically querying a non existent source, remove the relevant ppa file from /etc/apt/sources.list.d/ - if you are not sure how to just post back.

---

