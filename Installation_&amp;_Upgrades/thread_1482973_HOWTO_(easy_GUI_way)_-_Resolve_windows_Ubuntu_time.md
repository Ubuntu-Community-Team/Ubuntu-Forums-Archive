---
title: "HOWTO (easy GUI way) - Resolve windows Ubuntu time conflicts."
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2010-05-14
Your hardware clock (from the BIOS) might have 2 sorts of times - 

GMT/UTC or 
Localtime

Most probably it is localtime; but when installing Ubuntu, it doesn't ask you anything like that; as a result you set the timezone to your location and Ubuntu shows you the wrong time while windows the correct time (since it assumes the hardware clock to have the localtime while Ubuntu assumes it to be GMT).

The simple graphical solution to set your timezone to Europe/London; since it's at UTC+0, Ubuntu will show local time there after. Thus people of London will never have this time problem and so will never come here (except the mods maybe).

To change your timezone after the installation goto system>administration>time and date.

There click on the lock below and set your time zone.

---

### Post by luvr on 2010-05-14
> **dE_logics said:**
> The simple graphical solution to set your timezone to Europe/London
But what about Daylight Savings Time (DST), then? Surely, the **Europe/London** timezone will use DST, won’t it? Wouldn’t you still run into the time offset issue while DST is in effect, then?

Even more complex: What about the southern hemisphere, where the seasons are the other way around? They will have DST when we don’t, and vice versa.

In addition, what happens if your computer’s clock gets updated through NTP (network time protocol)—which I believe Ubuntu does? Wouldn’t the clock be set to actual London time, then? (After all, you **do** claim that your local time actually *is* London time!)

In my humble opinion, a far better solution is to simply not lie about your local time. If you have a need to set your hardware clock to local time (instead of UTC), because that’s how Windows wants it, then you had better *“make Ubuntu use Local Time,”* as documented on the [UbuntuTime - Community Ubuntu Documentation]("https://help.ubuntu.com/community/UbuntuTime") page:
> **_Make Linux use ‘Local’ time_**

To make your Ubuntu system read the hardware clock as ‘local’

[LIST=1]
[*]edit /etc/default/rcS
[*]add or change the following section
```
# Set UTC=yes if your system clock is set to UTC (GMT)
      UTC=no
```[/LIST]
Granted—this is not an *“easy GUI way”*... But it does **resolve** the issue, rather than attempting to circumvent it.

---

### Post by dE_logics on 2010-05-16
Humm...never though about DST (we don't use it).

Anyway, thanks for the tip.

---

