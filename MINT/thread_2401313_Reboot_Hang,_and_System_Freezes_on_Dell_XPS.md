---
title: "Reboot Hang, and System Freezes on Dell XPS"
date: 2018-09-16
forum: MINT
---

### Post by guguma2 on 2018-09-16
Hi All,

The issues I am having are with a Linux Mint 19, but the mint community is not as active and I believe this to be a core issue than a distro issue.

1) After I install Mint 19, using Ubiquity, the system hangs on Reboot.

2) When I login to the system, hardware related terminal commands ,eg., inxi -F also freezes the system, as well as running rhythmbox or any music player daemon software. And reboot freezes as well.

I managed to get inxi -f and rhythmbox running by using the kernel parameter 

```
acpi=off
```

or

```
acpi_rev_override=1
```

acpi=off seems to work better.

However my system still does not reboot properly. I saw something along the lines of "rebooting the freshly installed LIVE something something" on one of my reboot attempts (since the system never rebooted properly after the fresh install, is this a leftover???)

Installing nvidia-driver-390 seems to work, however my systems fans are blasting at full speed when i do that. I tried Nvidia v396, but then the drivers does not work at all.

I am completely at a loss here regarding what is going on, I am have meddled with Linux quite a bit back in the day but a lot of things seems to have changed and I do not understand much.

Your assistance would be much appreciated.

---

### Post by wildmanne39 on 2018-09-16
*Thread moved to **MINT for a more appropriate fit**.*

---

