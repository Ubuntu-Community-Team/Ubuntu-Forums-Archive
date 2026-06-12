---
title: "after several updates no /var/run/reboot-required but machine behaving a bit buggy"
date: 2016-05-27
forum: Installation &amp; Upgrades
---

### Post by roberto32 on 2016-05-27
hi everybody, I recently have few updates  but no "need to restart" pop-up appeard, also no existence of /var/run/reboot-required. Was it really like that? that no reboot was required. seem kinda strange and my machine was also behaving a bit buggy like - volume button ddidn't work.... (so it need an update apparently)
I chceck whether I've been pwned - netstat, system logs nothing suspectible.
Also system and security updates were included (I've some "non-standard" repo) but not the proposed.
And at last there's no  /var/log/auth.log is void - I login in terminal as a admin there's still nothing in that file? a bug??

---

### Post by Impavidus on 2016-05-27
Most updates don't require a reboot. Typically, only kernel upgrades require one and I haven't seen any of those in the past few days. Your volume control button may need an upgrade, but that may not be available yet. So nothing strange until now.

As for /var/log/auth.log being empty, that's peculiar. Plenty of stuff gets logged there. The log should be rotated automatically. Maybe it just got rotated? Should then be in auth.log.1. Maybe someone else can shed some light on that.

---

