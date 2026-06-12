---
title: "Disk error 01, AX = 4240, drive 9f (FIX)"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by Floydius on 2008-10-16
I noticed that in [some]("http://ubuntuforums.org/showthread.php?t=718368&highlight=disk+error+01%2C+AX+4240%2C+drive+9F") [archived]("http://ubuntuforums.org/showthread.php?t=364342&highlight=disk+error+01%2C+AX+4240%2C+drive+9F") [discussions]("http://ubuntuforums.org/showthread.php?t=286036&highlight=disk+error+01%2C+AX+4240%2C+drive+9F"), the following error was reported when trying to boot the liveCD:

```
Disk error 01, AX = 4240, drive 9f
```

I ran into this as well on a computer I was fixing, and noticed that when I had either (a) no HD plugged in at all or (b) a bad HD, it would give me this message.  Once I attached a good HD to the master IDE cable, the error was gone completely.  Hope this helps someone.

The BIOS I was using was Award 6.00PG, and I could not find a firmware update for it.  Not sure the make/model of the mobo since it is an old computer with no obvious markings on the mobo.

---

