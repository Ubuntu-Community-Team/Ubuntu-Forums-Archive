---
title: "Boot problem"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by ehajj on 2006-10-09
[B]Here's my problem:

I got windowsXP on my machine, then I got a new hardisk and 10 copies of ubuntu, so I plugged the new HDD as slave and installed ubuntu. Now when I start my pc I get OS choice from ubuntu (grub). I got a new machine just for Ubuntu and I want to remove the slave HDD where ubuntu is installed to put in on the standalone machine. When I do that, I can't load my WindowsXP OS on the old machine. How can I fix that without loosing any data from WindowsXP.[/B]

---

### Post by Kateikyoushi on 2006-10-09
Boot from the windows cd.
Go to recovery console and type fixmbr.

---

### Post by ehajj on 2006-10-09
**But if I do that, won't I loose any information from any partition?**

---

### Post by Kateikyoushi on 2006-10-09
No, that only effects the Master Boot Record not your partitions.

[More info here]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true").

---

