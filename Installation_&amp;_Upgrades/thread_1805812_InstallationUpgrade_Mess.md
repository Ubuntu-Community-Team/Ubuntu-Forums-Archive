---
title: "Installation/Upgrade Mess"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by anachronon on 2011-07-16
Hey all; it's me again--back with the same problem.  Here's the story:  About a month back, my updater tried to install a new, ext4 distro onto a partition that was formatted for ext3.  Needless to say, it turned my kernel into an unusable mess.  So, I tried a clean install, off of a CD.  But, thanks to my now corrupted file system, the installer made an even bigger mess, even corrupting my GRUB partition.

Well, after some work, I was able to get the Windoze OS to boot again.  But, I can't get the Linux installer to recognize the either the GRUB or old Linux partitions.  There is no damage to any of the partitions, other than now being filled with meaningless gibberish.

Is there a way to get the installer to "see" these partitions, so that it can reformat them and install the OS?  I am trying to go with "Ubuntu Studio", whose installer uses a text-only interface.   I have a partition utility.  But, it has goes up to ext3--not ext4.  Plus, what file system would I use to reformat the 2.5G GRUB ("SWAP") partition?  Or, should I just reformat everything back to Windows, and start a fresh Linux install?

---

### Post by anachronon on 2011-07-19
No one has any ideas or suggestions?

---

