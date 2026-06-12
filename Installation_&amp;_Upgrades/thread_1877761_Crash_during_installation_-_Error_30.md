---
title: "Crash during installation - Error 30"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by rihard_marius on 2011-11-08
I am trying to install Ubuntu 11.10 i386 to the desktop. The installation failed with following information:


 The installer encoutered an error copying files to the hard disk:
 [Errno 30]Read-only file system: '/target/boot/vmlinuz-3.0.0-12-generic'
 

This is often due to a faulty hard disk. It may help to check whether  the hard disk is old and in need of replacement, or to move the system  to a cooler environment.
 

I am wondering if there is any other solution that I needn't replace the hard disk. Or the hard disk is only the problem.


Thanks


**EDIT**

I shut down the computer, take out the panels and wait 20 min to cool down.

Re-tried to install and now I get at the beggining of the insallation:

"ubi-partman failed with exit code 141
more info in /var/log/syslog"

rebooted and tried to open a live session, it loads but it stops with the violet background with the cursor.
i can move the cursor but there is no panel or icons, right click doesn't do anything.
i can press ctrl+alt+f1 and i can use the terminal.
i ran fsck, fsck sda, fsck -a, etc, everything returned fsck util in universe (or something)

already tried with a 11.04 live cd, same answer: ubi-partman failed with install, freeze with live session

Thanks

---

