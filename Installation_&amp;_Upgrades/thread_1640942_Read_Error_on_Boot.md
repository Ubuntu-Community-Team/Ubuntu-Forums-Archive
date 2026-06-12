---
title: "Read Error on Boot"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by temjerk on 2010-12-08
I was in class today and my file manager stopped responding. I would click to open Documents and it would hang with "Documents Opening" and then the task bar item would disappear. I figured it was a transient problem and rebooted but after rebooting it went through my bios load screen and then just displayed "READ ERROR".

My old Windows HDD works fine when I put it it in, but after many attempts I can't get Ubuntu to boot. Does anyone have any idea what could be causing this? Is my HDD dead?

---

### Post by oldfred on 2010-12-08
Welcome to the forums.

Hard drive could be the issue.

From liveCD you can go to system, administration, Disk Utility click on the drive in the left panel and on the right is smart data. See if it reports errors.

You can also try this, change sdb1 to each of your linux partitions if more than one:
From liveCD so everything is unmounted, change sdb1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

