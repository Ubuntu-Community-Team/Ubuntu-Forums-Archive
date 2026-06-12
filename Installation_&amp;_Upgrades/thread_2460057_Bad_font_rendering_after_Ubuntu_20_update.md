---
title: "Bad font rendering after Ubuntu 20 update"
date: 2021-04-01
forum: Installation &amp; Upgrades
---

### Post by dangeloguillermo on 2021-04-01
So, the words on the terminal and windows (folder names) are trimmed up to four characters, after an update performed yesterday.
How can I fix this?


[ATTACH=CONFIG]288207[/ATTACH]

---

### Post by Impavidus on 2021-04-12
Keep an eye on this thread: [URL="https://ubuntuforums.org/showthread.php?t=2460487"]https://ubuntuforums.org/showthread.php?t=2460487
[/URL]It appears to be the same issue.

---

### Post by guiverc on 2021-04-12
Ubuntu 20?  There is no such release.

Ubuntu uses *yy.mm* format (*year.month* of release) for all server & desktop releases, the *yy* being used only for IoT and specialist appliance/device releases (also suitable for cloud use) that can use *snap* packages only.  

By Ubuntu 20 do you mean Ubuntu Core 20?  as it's a different product to Ubuntu 20.04 LTS (desktop or server), but can be used with the GNOME *snap* installed on it, thus a desktop of sorts too...

---

### Post by ActionParsnip on 2021-04-12
If you are unsure then please give the output of:
```

lsb_release -a; uname -a

```
Thanks

---

