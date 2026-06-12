---
title: "Slow boot time"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by J Blain on 2012-03-01
On my portable computer Alienware M11x running Ubuntu, any kernel version after 3.0.0.12 boots up in an appallingly slow fashion.

3.0.0.12 will boot at least 3 or 4 times faster then any of the newer kernel. Any idea what changed post 3.0.0.12 that would explain this ?

Newer kernels are of course nice but until I figure out why booting them is so slow it will be hard to switch. The newer kernels bring me back to the old windows days and that is no good...

---

### Post by dino99 on 2012-03-01
To let you know when/where it "freeze" while booting, remove "splash" by editing the boot line on grub menu. That way you get the verbose mode and will see warnings/errors explaining why its so slow.

Of course glance at xsession-errors inside /home & /var/log/ for the dmesg & kern.log

---

### Post by J Blain on 2012-03-01
> **dino99 said:**
> To let you know when/where it "freeze" while booting, remove "splash" by editing the boot line on grub menu. That way you get the verbose mode and will see warnings/errors explaining why its so slow.

Of course glance at xsession-errors inside /home & /var/log/ for the dmesg & kern.log

It freezes on high speed usb device 4 for a very long time and then continues, this seems to be associated with my synaptic touchpad.

Any suggestions ?

---

