---
title: "HP Microserver doesn't boot after 2.6.38 kernel upgrade"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by chortya on 2011-07-15
Upgraded from 10.10 to 11.04. Worked some time but then aufter another kernel upgrade the server stopped booting. I tried the workarounds posted here (regarding graphics) but nothing helped. Old 2.6.35 kernel boots just fine.

Problem:
Grub works, but after booting 2.6.38-10 kernel server instantly freezes with NO VGA output. No splash screen or other messages before freeze. Selecting older 2.6.35 kernel from the grub subemenu lets me start the server.

Questions:
- how do I downgrade to older kernels permanently (e.g. 2.6.37)?
- how to select in Grub old kernel from submenu as default? Exact submenu name in /etc/default/grub didn't work...
- what is the right way to diagnose boot problems, what logs should I check?

Thanks

---

### Post by Ashrael on 2011-07-15
I have problems too after installing that same kernel :confused:....
You could boot from cd and investigate the log files to figure out your problem.
Maybe this post can help too:   [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

My wifi connection is my most obvious problem...See:

[http://ubuntuforums.org/showthread.php?p=11049752#post11049752](http://ubuntuforums.org/showthread.php?p=11049752#post11049752)

You are not alone!

Any more problems with this kernel out there? Anyone?

---

