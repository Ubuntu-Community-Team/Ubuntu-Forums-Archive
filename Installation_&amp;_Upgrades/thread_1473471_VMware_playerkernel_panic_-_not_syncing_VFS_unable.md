---
title: "VMware player::kernel panic - not syncing: VFS: unable to mount root................."
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by newbee_ on 2010-05-05
Hi,

I am relatively new in Ubuntu. I have following problem:

I recently started to use Ubuntu in VWware player on my windows-XP.
I installed ubuntu 10.04 few days ago, It was working fine.

Yesterday, I compile a new kernel, kernel 2.6.33 in my vmware ubuntu 10.04. Everything went well till I did reboot. before reboot I use the command "update-grub" to make it compatible to the new kernel. BUT... after rebooting, I have a problem in loading a grub correctly. it gives me following message "  [2.149136 ]kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)" and I can not proceed further. I have my all data on it. I also tried to boot it from live CD but unfortunately, I can't  mount the hard disk on it in order to get those data from my old Ubuntu set up.

I guess, There must be some way to come out of this. I checked all the forums but count not find the correct solution. I would appreciate if it's possible to get those data back in some way then, I'm ready to reinstall ubuntu. 

I would really appreciate all the member if you I get a help to come out of this.

Any suggestion?

Thanx,

---

### Post by dr_latino999 on 2010-05-05
I'm experiencing the same issue as the OP. Using kernel x.33, in VMWare Workstation 7.0 / 7.1 beta, and ESX 3.5i I return the kernel panic error.

---

### Post by newbee_ on 2010-05-05
[Hi dr_latino999]("http://ubuntuforums.org/member.php?u=832399")                 

At least I got reply...... thanx...

Have you found out how to deal this issue?

I hope we come over this problem soon.....

regards,

newbee_

---

### Post by dr_latino999 on 2010-05-05
> **newbee_ said:**
> [Hi dr_latino999]("http://ubuntuforums.org/member.php?u=832399")                 

At least I got reply...... thanx...

Have you found out how to deal this issue?

I hope we come over this problem soon.....

regards,

newbee_
Newbee, I'm going to try and install the system on metal and see if it's an issue with the virtualization process. Unfortunately it's an old P4 box so the compile will take about 9 hours so I won't be able to provide any concrete results until tomorrow.

---

### Post by dr_latino999 on 2010-05-05
Newbee, right before I left work the system installed and successfully rebooted on metal. Spent 15 minutes pruning the kernel and saved 7 hours on the compile :) It has to be an issue with how kernel 2.6.33 interacts with the hypervisor.

---

