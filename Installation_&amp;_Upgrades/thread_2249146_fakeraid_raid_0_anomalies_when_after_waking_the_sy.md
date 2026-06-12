---
title: "fakeraid raid 0 anomalies when after waking the system up/power it on"
date: 2014-10-19
forum: Installation &amp; Upgrades
---

### Post by piadex2 on 2014-10-19
Dear Forummates,

When there is no Ubuntu on my fake raid 0, just windows 7 (or XP), everything is fine. But when I install ubuntu (latest version) these sympthoms appear:
1. If I shut down my PC ("shut down") and then trying to start it it says my disks are offline members.
To make them be online again: I need to boot from ubuntu live then:
```

sudo apt-get install dmraid

```
then restart (instead of shut down). And at the next boot my disks are online again GRUB appeares and so...
2. If I make windows 7 (pro) sleep and then trying to wake it up I get:
a "PC is locked screen" but at this point it freezes totally. I need to do push the reset button.
And I get one online and one offline member.
To solve this I need to do the previous trick but this time not only once but two times. After doing that Everything works.

Why is this and what to do to make my system run as it should be?

Thank You for Your help in advence.

piadex2

---

