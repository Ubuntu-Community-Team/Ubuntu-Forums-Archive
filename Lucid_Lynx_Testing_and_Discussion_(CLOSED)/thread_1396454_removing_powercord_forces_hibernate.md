---
title: "removing powercord forces hibernate?"
date: 2010-02-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by puccaso on 2010-02-02
this is a nasty thing..

how do i fix it, or where can i start looking?

whenever the plug is removed, ie i want to move to another room or something, the laptop just goes to hibernate... and because this is a hp 2133, hibernate takes a damn long time..

how do i stop this from happening?


thanks all..

---

### Post by Grenage on 2010-02-02
Are you closing the screen when you unplug the power? Either way, take a look in power management.  It has profiles for mains and battery power.

---

### Post by autark on 2010-02-02
It could be that your power manager thinks the battery is very low and therefore does an emergency hibernation.

---

### Post by dfme on 2010-03-27
I have the same issue. The battery is fully charged and whenever i remove the power cord the system says there is power for 2 minutes remaining! It then hibernates...
When resuming the battery applet says my battery has power for at least 2 hours!
I am using Ubuntu Lucid 10.04

---

### Post by m.rankovic on 2010-03-27
Same here on MSI Wind U100, as a workaround (works for me): unplug the power cord, logout before it hiberntes then log back in.

sry for bad english...

---

### Post by dfme on 2010-03-29
> **m.rankovic said:**
> Same here on MSI Wind U100, as a workaround (works for me): unplug the power cord, logout before it hiberntes then log back in.

sry for bad english...
I also have this issue on a MSI Wind U100! Do you know if there's already a bug report for this? This should be fixed... your described workaround isn't really viable since my mother-in-law uses the machine :-P

---

### Post by dfme on 2010-03-29
Hmm... Maybe I could have just searched this myself=D
I have found some matching bug reports:
[https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/481056](https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/481056)
[https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/504929](https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/504929)

you can also report your experiences there
cheerio

---

### Post by sahilsinha on 2010-04-06
I am having the same issue on a no name laptop, everything was fine under Karmic.

---

