---
title: "full speed fan after nvidia driver install"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jaci87 on 2009-10-25
Hi all,
after installing nvidia 185 drivers for my GeForce 8400M GS, I've experimented the following issue: when gdm appears, fan starts running at full speed and keeps going on for a few minutes. Then it returns to low speed...this obviously happens on resume from suspend/hibernation and when logging out.
I tried old 173 drivers and this not happens, instead 190 beta are like 185.

Any suggestion?

P.s.: sorry for my bad english. :mad:

---

### Post by jaci87 on 2009-10-26
bump

---

### Post by tribaal on 2009-10-27
Same card, same problem here.

Here's my relevant lspci info:

```
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
```

Hope this helps. Couldn't find any relevant bug on launchpad, jaci87 if you filed one please give me the bug number so I can track it too.

Cheers,

- Trib'

---

### Post by jaci87 on 2009-10-28
I didn't filed the bug, but I opened a thread in official Nvidia Linux Forum: [http://www.nvnews.net/vbulletin/showthread.php?t=140507](http://www.nvnews.net/vbulletin/showthread.php?t=140507)
As far I can see, it's driver related and seems to involve 8400M cards. :(

---

### Post by ioka on 2009-10-28
> **jaci87 said:**
> I didn't filed the bug, but I opened a thread in official Nvidia Linux Forum: [http://www.nvnews.net/vbulletin/showthread.php?t=140507](http://www.nvnews.net/vbulletin/showthread.php?t=140507)
As far I can see, it's driver related and seems to involve 8400M cards. :(

you should use nvclock from the repos. run this.

```
 sudo aptitude install nvclock && nvclock -f -F 60
```

---

### Post by jaci87 on 2009-10-29
I've already tried in the past, nvclock gives me a laconic:
```
Error: Your card doesn't support fanspeed adjustments!
```

---

