---
title: "Volsnap.sys bluescreen issue after installing ubuntu"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by sega16 on 2012-10-09
I have installed ubuntu on my computer and a friends computer without any issues and then another friend also wanted ubuntu after seeing how much better it preforms compared to windows. So I installed it on there computer and they needed to run a windows only program and we got a bluescreen error that had to due with volsnap.sys. At first when I tried to install ubuntu on that computer I ran into an issue where install along side windows was not initially available that Gparted told me  to run to correct a duplicate sector issue and that was resolved and after that I was able to install ubuntu along side windows (I am not sure if this is relevant to the issue but you never know). I did do some research and it turns out that windows xp trys to access all partitions but why would it do that if windows can not access the ext4 file system I have no issues on the 2 other computer that I installed ubuntu on (I could be because they both ran windows 7 instead of xp) My idea for a solution would be to backup all important files and reinstall windows however my friend worried about losing data. Are there other ways to fix this or a way to convince my friend to reinstall windows. I do fell bad for messing up their computer. Here is my current partition setup if it helps anyone [IMG]http://imageshack.us/a/img41/3994/gpartede.png[/IMG]

---

### Post by goinglinux on 2012-10-10
> **sega16 said:**
> we got a bluescreen error that had to due with volsnap.sys. 
It turns out that volsnap.sys is a Windows system file that can become infected backdoor. Since you still have Windows on the sda1 partition, it is possible that the drive is infected with malware. Do the backup, then scan it with a malware detector to remove the infection. If that doesn't work, completely wipe the drive and reinstall Windows. After you scan the backed-up files for infections, restore the data files and reinstall Ubuntu.

---

