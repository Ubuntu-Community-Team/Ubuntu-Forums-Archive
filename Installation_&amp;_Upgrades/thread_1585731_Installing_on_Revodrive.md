---
title: "Installing on Revodrive"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by jkounis on 2010-09-30
There's a new drive that combines 2 SSDs in a RAID 0 configuration and comes as a PCI-Ex x4 card: [http://www.ocztechnology.com/products/solid-state-drives/pci-express/revodrive/ocz-revodrive-pci-express-ssd-.html](http://www.ocztechnology.com/products/solid-state-drives/pci-express/revodrive/ocz-revodrive-pci-express-ssd-.html).

According to the review at [http://www.guru3d.com/article/ocz-revodrive-120gb-review/12](http://www.guru3d.com/article/ocz-revodrive-120gb-review/12), the "SIS RAID controller is a semi-software based solution (I like to call that fakeRAID)".

Has anyone tried to install/boot Ubuntu on a Revodrive? Can grub see Raid0 partitions?

If grub can't see it, would one possible solution be to put /boot on a real HDD, and then use the RAID 0 SSD for / and /home?

---

### Post by P4man on 2010-10-01
It can boot linux according to OCZ
[http://www.ocztechnology.com/res/manuals/OCZ%20RevoDrive%2050GB-80GB%20Product%20Brief.pdf](http://www.ocztechnology.com/res/manuals/OCZ%20RevoDrive%2050GB-80GB%20Product%20Brief.pdf)

Interesting device BTW.

---

### Post by andy-tom on 2010-10-11
[http://www.ocztechnologyforum.com/forum/showthread.php?76486-Revodrive-Ubuntu-10.04-install-issues](http://www.ocztechnologyforum.com/forum/showthread.php?76486-Revodrive-Ubuntu-10.04-install-issues)

Read [**UncleJoe1985**]("http://www.ocztechnologyforum.com/forum/member.php?56279-UncleJoe1985&") 's posts.

---

### Post by GulDukat on 2010-11-29
Hello all,

I'm running Ubuntu 10.10 on a RevoDrive. It installs very nicely. Now this:

I want to dual boot Ubuntu with winxp on the revodrive. Although everything goes well during installation of ubuntu (if I recall, it was detected as raid 0), I am now not able to resize the ubuntu partition! GParted sees it as two seperate disks. This is the case for gparted on the live cd as well as run from ubuntu itself.

Is the RevoDrive raid 0 support built-in to the installer instead of into GParted? Any suggestions on how to resize my partition without actually having to reinstall Ubuntu all over again? (I figure I needed to save space for winxp in the first place but chose the wrong setting during installation).

GulDukat

---

