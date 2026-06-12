---
title: "[SOLVED] No First User Account Created?"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by VTStevenVT on 2008-01-27
I just installed Ubuntu 7.10 from the alternative cd. I had some issues during installation where I got a ton of vertical bars and had to start over, but on the second try I got through everything. Then when I started my ubuntu partition (I'm dual booting with XP) my monitor said the Screen Hz were out of range. I was able to start in recovery mode and fix that problem. Now I can't login to X or the other shells ( Ctrl + Alt + F2 ....). I stared in recovery mode and did [PHP]ls /home[/PHP] which is returning nothing. After some googleing and found  stuff on the 7.10 release wiki and it says to add my username to the system group with [PHP]addgroup --system admin[/PHP] This command tells me the admin group already exists so I type in [PHP]adduser MYUSERNAME admin[/PHP] and it tells me that MYUSERNAME does not exist. So it appears the first account I made during the installer was never created. How do I fix this?

-Steve

---

### Post by VTStevenVT on 2008-01-27
Fixed. I booted into recovery mode and reset the root password

[PHP]passwd root[/PHP]

Then Created my account

[PHP]adduser MYACCOUNT[/PHP]

And that was it

---

### Post by taurus on 2008-01-27
Did you happen to use the oem mode when you installed it from the alternate CD?

---

