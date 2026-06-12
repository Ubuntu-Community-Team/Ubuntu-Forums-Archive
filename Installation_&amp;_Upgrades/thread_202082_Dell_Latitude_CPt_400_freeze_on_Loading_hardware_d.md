---
title: "Dell Latitude CPt 400 freeze on Loading hardware drivers"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by mosestruong on 2006-06-22
I've installed xubuntu on an old Dell laptop, after getting through the installation process by adding using that "exclude" line, i thought all was good. It detected the PCMCIA network card without any problem.

But when I tried to start the computer again, it freezes when I get to "Loading hardware drivers".
If I remove the network card, then sometimes it will boot ok, and when I plug the network card back in, it detects it and everything works. However, I've just discovered that this sometimes doesn't work either - it will freeze at the same spot.

If I boot in recovery mode, it gets pass the hardware part, but then it freezes on "nm256: Mapping port 1 from 0x3f09a0 - 0x3fec00"

Sometimes, it will boot into level 1 single user mode, and if I type "init 5", then it works as normal...

Does anyone know whats going on or know how I can resolve this problem.
Thanks.

---

### Post by wbmj on 2006-06-22
The NeoMagic Driver issue has been around for awhile. There still doesn't seem to be a viable fix. You can blacklist the sound driver and you won't have the freezing anymore. However you won't have any sound either.

---

### Post by mosestruong on 2006-06-22
[QUOTE=wbmj]The NeoMagic Driver issue has been around for awhile. There still doesn't seem to be a viable fix. You can blacklist the sound driver and you won't have the freezing anymore. However you won't have any sound either.[/QUOTE]

Thanks for your reply. I was constantly thinking it was the PCMCIA card that was the problem... but now, realised its the sound thats the problem, and found a solution for the problem at [http://ubuntuforums.org/showthread.php?t=90336]("http://ubuntuforums.org/showthread.php?t=90336")

---

