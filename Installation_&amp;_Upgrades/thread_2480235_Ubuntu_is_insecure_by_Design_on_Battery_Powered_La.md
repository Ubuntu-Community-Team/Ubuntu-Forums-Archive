---
title: "Ubuntu is insecure by Design on Battery Powered Laptops ?"
date: 2022-10-23
forum: Installation &amp; Upgrades
---

### Post by johnfoss on 2022-10-23
Sorry to say but I have no clue why Ubuntu is desinged insecure for all battery-powered Laptops.

Normal use Case in my family and at work is:
mobile Work with battery - charge at Night.
In these Cases ubuntu basically never/seldem runs unattended Upgrades.

Reason
1. There are two apt timers which run only on AC power
- apt-daily.timer runs /usr/lib/systemd/system/apt-daily.service for "Daily apt download activities" (runs apt update)
- apt-daily-upgrade.timer runs /usr/lib/systemd/system/apt-daily-upgrade.service for "Daily apt upgrade and clean activities" (runs unattended-upgrade)
bouth scripts have "ConditionACPower=true" set so unattended upgrade never starts.

2. There is an additional check in /etc/apt/apt.conf.d/50unattended-upgrades:
```
// Download and install upgrades only on AC power// (i.e. skip or gracefully stop updates on battery)
Unattended-Upgrade::OnlyOnACPower "false";
```

For now i have to
run
> sudo systemctl edit apt-daily.service
> sudo systemctl edit apt-daily-upgrade.service
and set > ConditionACPower=

---

### Post by yancek on 2022-10-23
I expect that is because of the fact that many people run updates on battery power and the power dies and the update crashes and that leads to other problems.  Many posts here where that has happened.  Why not modify the scripts you refer to?  I don't think this is Ubuntu specific, other OS's do the same.

---

### Post by Impavidus on 2022-10-23
Only running automatic upgrades when on wall power (and not on a metered internet connection) makes sense. Downloading and installing upgrades can take quite a bit of energy and it's especially problematic if the battery runs down while installing upgrades, leading to an interrupted upgrade and possibly unbootable system. Your usage pattern of never using Ubuntu with the laptop plugged-in may not be typical. However, if you think that there should be an option with a checkbox in the upgrade settings tot override this, feel free to file a [bug report]("https://help.ubuntu.com/community/ReportingBugs").

I think you may still get a warning if you don't check for upgrades in a long time, suggesting you do it manually.

---

### Post by ajgreeny on 2022-10-23
An alternative, of course, is to completely disable unattended upgrades, which I do by removing the package from my systems.

OK, it means I have to upgrade daily or at least very often, but I check first thing always when I start using my computers using command line only and it takes very little time.

---

### Post by johnfoss on 2022-10-25
I corrected my workaround instead of commenting out you have to explicitly set Nothing “ConditionACPower=”


You all have good points, maybe the whole upgrade process needs more intelligence then.
Check if battery is 30% at least or AC powered, then start (security) upgrades.

Anyway, normal SSD laptop upgrades for all origins are done in less than 2 minutes if they run regularly.
Maybe the fact that there are so many interrupted upgrades is due to running upgrades too rarely?

Some of the people I deploy ubuntu laptops don’t know how to manually upgrade and they are not willing to learn this stuff because they don’t care...

---

### Post by Impavidus on 2022-10-25
Maybe it would be best to have an option that, when enabled, allows automatic upgrades when the battery is at least 50% charged at the time the upgrade starts. That would make it very unlikely to run out of battery while upgrading.

---

