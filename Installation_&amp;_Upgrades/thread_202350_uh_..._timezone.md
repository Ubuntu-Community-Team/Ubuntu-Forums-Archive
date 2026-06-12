---
title: "uh ... timezone?"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by dmizer on 2006-06-23
okay ... i needed a server install of dapper on one of my boxes for testing, so i downloaded the alternate install cd.

i selected a us/english language pack and keyboard.  but when i have to select a time zone, it won't let me select a time zone outside of the us.  and since i live in japan (and will be for many years) ... i'd like to be able to select a timezone relative to where i live on the planet.

i'm sure i will be able to correct this later, but strange that this is not an option on install of ubuntu.

---

### Post by aysiu on 2006-06-23
What do you mean it won't let you? The option appears but is greyed out? Or the option doesn't appear at all?

Try ```
sudo tzconfig
```

---

### Post by dmizer on 2006-06-24
on system install, the only options i have for time zone are us time zones.  there are no other options in the list.

this would be the ubuntu-6.06-alternate-i386.iso image.

of course after install and doing "sudo tzconfig" i was able to select my correct time zone.  but i thought it was strange i was unable to do this on install.

---

