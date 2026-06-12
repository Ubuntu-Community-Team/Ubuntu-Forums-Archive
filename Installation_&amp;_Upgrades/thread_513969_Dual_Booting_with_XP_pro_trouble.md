---
title: "Dual Booting with XP pro trouble"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by RevJonathan on 2007-07-31
Ok, so I was running just fine a while ago when Ubuntu let me easily resize my XP pro partition and install Ubuntu. However, Ubuntu went under crashing the whole drive. Here's the twist-
My manufacturer's recovery disk formats the WHOLE hard drive and sticks XP right at the front, so Ubuntu can't resize the partition automatically. There's no way around this install method for XP. I can't use System Rescue disk, because it won't support the ATI drivers on my laptop.

I like Ubuntu and I'd like to have it on my laptop, but I still need XP for work. How am I supposed to do this?

Thanks,
Rev.

---

### Post by Netsurfer on 2007-07-31
You have to manually resize your partition.
You can use opensource **QTParted ** program (It is included on Knoppix Live CD).

See at this site: [http://www.cyberciti.biz/tips/how-do-i-resize-windows-partition-with-open-source-software.html](http://www.cyberciti.biz/tips/how-do-i-resize-windows-partition-with-open-source-software.html)

Bye

---

### Post by D4mn on 2007-07-31
You can also try this [http://www.sysresccd.org/](http://www.sysresccd.org/). Perhaps not using your vendor's recovery cd to install XP is not the way to install Windows but of course that is entirely up to you...

---

### Post by RevJonathan on 2007-07-31
Hey guys,
I realize I need to manually partition it, but I am afraid I am not that tech savvy. I tried using System Rescue CD, but my laptop uses an ATI driver, redering them useless for my partitioning, as I cannot startx. Will I need to use another partition manager? If so, what's a good text-based, or ATI-compliant partitioning tool?

I would use another disc windows install, but I'm afraid I'm unable to use one.

---

### Post by D4mn on 2007-07-31
Hi, there is CLI partition editor called parted :)

If you do not have the command, execute **sudo apt-get install parted**, but I am quite sure it is available from a default installation (did not check it).

Good luck!

---

