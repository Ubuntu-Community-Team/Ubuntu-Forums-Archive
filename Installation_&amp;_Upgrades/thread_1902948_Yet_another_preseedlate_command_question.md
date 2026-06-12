---
title: "Yet another preseed/late_command question"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by shayc on 2012-01-01
Hi, 

I am trying to use preseeding in order to manage automated installation of Ubuntu 10.10 .
After successfully getting the installer using a seed file, including all the 'answers' , installing from a remote LAN repository , etc - I still can not get the commands listed after 
preseed/late_command (and preseed/early_command for that matter) running. 

My preseed file ends like this: 
d-i preseed/late_command string in-target touch /tmp/lfile;
I also tried: 
d-i preseed/late_command string touch /target/tmp/lfile;
both with and without the semi-colon. 

For what it worth, the only *_command directive I did manage to get actually running, is the partman/early_command. 

Any ideas ? 
(Please don't be too harsh if it's something VERY silly :) )

Thanks in advance, 
Shay

---

### Post by shayc on 2012-01-01
Small update: 
under /var/cache/debconf/config.dat preseed/late_command is marked as template: debian-installer/dummy. 

Anyone knows what can cause that ?

---

