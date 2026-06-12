---
title: "'Install' can't see my partition."
date: 2020-01-24
forum: Installation &amp; Upgrades
---

### Post by richard-261 on 2020-01-24
Hello
I'm new to Ubuntu and trying to install it as a dual boot with W7.
I've made a partition of 25G in W7 then run the Ubuntu install from a DVD that I burned.
Install can see the partition that W7 is on and other 'storage ' partitions, but not the 25G partition that I want to use for Ubuntu.
Ubuntu is working from the DVD so I can see in 'file manager' that the 25G partition is there, but its not visible in Gparted. 
Am I doing something wrong?
Any help will be appreciated.
Richard

---

### Post by oldfred on 2020-01-24
Most Windows 7 systems uses the old MBR partitioning. That has a 4 primary partition limit. 
One primary partition must then be the extended partition which then acts as a container for as many logical partitions as you may want. 

Post this:
sudo parted -l

My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

---

### Post by richard-261 on 2020-01-25
Thank you for the reply. That sounds like the answer. I'll have a go later.
What I found really confusing was that while using Ubuntu from the DVD, Ubuntu could see the 'missing partition' in 'Files' But not in 'Gparted' or 'Install'.
Anyway, thank you again, I hope to be up and running later.
Richard.

---

