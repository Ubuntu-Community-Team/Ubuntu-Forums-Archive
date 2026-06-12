---
title: "Unable to upgrade 10.04 to 12.04"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by kumarat9pm on 2015-08-17
Hi team,

            I am facing a strange issue when upgrading 10.04 to 12.04. We are doing this as a part of upgrading our 200 servers from 10.04 to 14.04 as 10.04 is no more supported. I am doing this change in our lab where I can test multiple times. The issue is middle of upgrading(I used do-release-upgrade command) my system reboots with out any conformation. After reboot, it will not boot properly and fails with different errors. My question is why my upgrade requires a reboot and that too middle of installing some packages which I feel is a bit strange issue.

Any suggestions on this?

---

### Post by dino99 on 2015-08-18
the reboot issue can be due to the grub -> grub2 transition : the old grub menu.list need to be purged as it can do weird things with grub2 (grub-pc)
so purge grub* and install grub-pc on the mbr partition (/dev/xxx)

avoid rebooting if the upgrade is not complete as it will then be a nightmare to fix the issues. Instead call ctrl+alt+f2 to do manual commands, then ctrl+alt+f7 to return on main.

how do you upgrade all the servers at once ?
[http://www.linux.com/learn/tutorials/413853-managing-multiple-linux-servers-with-clusterssh](http://www.linux.com/learn/tutorials/413853-managing-multiple-linux-servers-with-clusterssh)
[http://xmodulo.com/how-to-run-command-on-multiple-servers-at-once.html](http://xmodulo.com/how-to-run-command-on-multiple-servers-at-once.html)

---

