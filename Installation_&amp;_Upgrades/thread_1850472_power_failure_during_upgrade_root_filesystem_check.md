---
title: "power failure during upgrade: root filesystem check failed"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by sowdust on 2011-09-26
Hello,

I was uprgading my 10.04 to 11.04 on my laptop; I was sure this was plugged in, while it actually wasn't: of course the power ran out during the upgrade process and therefore interrupted it. Now whenever I try to boot the system an error tells me that "Root filesystem check failed" and all I can do is use the shell (not the dpkg process that fails because of the apparently read-only nature of the filesystem).
I tried to look into my /home folder and everything seems to be still there, which is what I cared the most about; now I was wondering if there is a better and safer way to continue the upgrade than formatting the non-home partitions and re-install the operating system from zero, losing all the previously installed applications and their configurations. 

Thanks in advance for any suggestion

---

### Post by raja.genupula on 2011-09-26
hi, here you have a solution.

[http://www.streamreader.org/askubuntu/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation](http://www.streamreader.org/askubuntu/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation)

& 

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/154945](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/154945)

both are going to work

---

### Post by sowdust on 2011-09-27
thank you very much for the suggestion!
this method worked fine:

```

# mount -o remount,rw /
# dpkg --configure -a
# mount -o remount,ro /
# sync
# reboot
```

---

