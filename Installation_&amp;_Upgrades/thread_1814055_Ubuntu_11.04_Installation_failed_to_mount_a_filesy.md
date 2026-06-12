---
title: "Ubuntu 11.04 Installation: failed to mount a filesystem with type swap"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by nukeboy on 2011-07-28
Hi,

Normally I would search for days to find a solution, but time is not on my side these days, and google couldn't provide me with an adequate answer, so I come to ask you guys for help.

The situation is as follows. I have a 560GB HDD with Windows 7 on it, and I would like to dual boot it with Ubuntu 11.04. But a problem arises when the installation of Ubuntu tries to make the swap area (I guess) because the following error is given:

"The attempt to mount a filesystem with type swap in SCSI2(0,0,0), partition #6(sda) at none failed"

This problem has occured everytime I tried to install it on my desktop. I even bought a new HDD for it, because I thought the problem was the drive. I used the same installation USB key on my laptop, also dual booted with Windows 7, and this went fluently. I also tried to manually make the partitions, but those failed as well. Though, I must admit, I am not an expert in this, so I might not have tried every possible partitioning.

Can anyone help me further with this problem please? :confused: I thank you for your time.

---

### Post by quattro_cs on 2011-09-13
I had this same issue. The workaround I did was to close the installer, then open GParted. I created the partitions in there, then restarted the installation and simply used those partitions without reformatting. Worked like a charm.

---

### Post by bunfaloo on 2011-09-23
> **quattro_cs said:**
> I had this same issue. The workaround I did was to close the installer, then open GParted. I created the partitions in there, then restarted the installation and simply used those partitions without reformatting. Worked like a charm.

Sadly this isn't a great solution for some people.  After talking my mother into trying Ubuntu (because her needs are extremely minimal but she somehow keeps getting viruses and trojans on her system and HEY IT'S EASY TO INSTALL!1!) she can't get past this step.  More to the point, she lives in another country so I have to guide her through things remotely, and there's no way I'm going to have her fire up a disk partitioner without me looking over her shoulder because she could easily trash her system.

So much for the Ubuntu easy-install experience eh?  It failed at the first hurdle for the kind of user who needs it most.

---

### Post by smurphy_it on 2011-09-23
Can't boot up from the live media and then install something like "teamviewer 6" for remote control.  You then would connect to her machine, and do the installation for her ;-)

---

