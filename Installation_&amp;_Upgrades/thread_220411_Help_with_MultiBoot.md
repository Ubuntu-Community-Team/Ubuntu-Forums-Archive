---
title: "Help with MultiBoot"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by DThurman on 2006-07-21
Folks, I need a bit of help, perhaps someone can help?
Here's the deal.  I have the following Multiboot setup:

d1: p1[w98se], p2[w2kPro], p3[wXP], [Ext: [L1:App1], L2[App2]]
d2: p1[ubuntu:/boot], p2[ubintu:/], p3[debian:/boot], p4[debian:/]

With the above layout, I am able to multiboot everything except for Debian.  I am trying to figure out why my System Commander cannot even see Debian at all and so it cannot even add Debian to the internal list of supported linux distros.  I am guessing that system commander is unable to recognize debian p4 as a bootable partition, as I tried to tell SC it is bootable but SC refuses to accept that.

One extra tidbit: I did notice is that when I started up ubunto's grub command line and issuing the command: find /grub/stage1, grub could only find ubunto's root at hd1,0 but not at hd1,2. When I tried the grub command: root (hd1,2), grub reported an unrecognized linux journaling filesystem type 0x93 but it does recognize standard linux filesystem type 0x83.

So perhaps therein lies the problem?

I can think of two ways to resolve this issue:

1) Completely reinstall Debian but make sure that when defining the partitions that only filesystem type of 0x83 is defined.  The only drawback is that Debian installation or startup will fail since it insists on a fs type of 0x93 - i.e. it is required.

2) I may need to swap p3+p4 partition contents with p1+p2, reconfigure fstab & grub, and force MBR on d2 to that of Debian's grub so that debian's grub can understand both filesystem types (0x93 & 0x83)?  I note that from SC, it sees 0x93 partitions as type 0x83 filesystems and does not recognize type 0x93. I have SC v5.0 so perhaps this is a different problem.

But before I spend hours doing one of the two proposals, I would like to solicit for opinions of others here in this forum as to if what I am proposing makes any sense and perhaps there is another way?

Thanks for listening,
Dan

---

