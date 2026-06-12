---
title: "MP3 woes"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by UnderDark on 2006-09-03
Hello,

I've been using Ubuntu for about 3 months now.

This the 2nd time I've installed Ubuntu, and thus: already downloaded things like gstream0.8-*.

However, whenever I try to play an MP3 file, Totem tells me that it can not "Determine the type of stream"

Any ideas, or is my install borked?

---

### Post by andlinux21 on 2006-09-03
No your install is not borked but you may want to try EasyUbuntu or Automatix to install the needed codecs.

---

### Post by UnderDark on 2006-09-03
I found the problem:  "filesize: 0"

When I ran "mp3check -e ." it told that the mp3s in question where empty files.  After rumaging through some backups (CDs), I re-copied them, and I now have those pesky mp3s playing.

Some log searching told that the copy was aborted, but I guess it never cleaned up.

---

