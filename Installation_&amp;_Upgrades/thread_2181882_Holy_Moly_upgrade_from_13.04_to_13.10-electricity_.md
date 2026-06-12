---
title: "Holy Moly upgrade from 13.04 to 13.10-electricity was cut off upgrade interrupted"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2013-10-19
I was upgrading from 13.04 to 13.10 went the electricity was cut off.
and the installation was stoped so now when I start the ubuntu then go to recovery mode then try to run dpkg I get the following message
"/lib/recovery-mode/recovery-menu: line 76: /etc/default/rcS: No such file or directory".
How do I continuous from here ?

---

### Post by augustin-riedinger on 2013-10-19
Same problem here, except I didn't have an electricity cut. 
The install asked me override a file (that I suspect being /etc/fstab but I can't be sure about it) and I said yes. After reboot, I have a `Filesystem check or mount failed.`.
And in save mode, I get the same message 
[COLOR=#000000]"/lib/recovery-mode/recovery-menu: line 76: /etc/default/rcS: No such file or directory".
[/COLOR]when running fsck in safe mode console.

Thanks for any help!

---

### Post by buzzingrobot on 2013-10-19
Sounds like doing another clean install is in order. When the power cut out, the installation stopped.

---

### Post by augustin-riedinger on 2013-10-20
The solution is there ! 
[http://askubuntu.com/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation](http://askubuntu.com/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation)
It saved me!

---

