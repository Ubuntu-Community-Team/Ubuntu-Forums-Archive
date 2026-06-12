---
title: "unistall kubuntu"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by claudioo on 2008-11-21
I have ubuntu and kubuntu on dual booting and like to unistall kubuntu 
I have no idea how to .

---

### Post by lemming465 on 2008-11-22
"uninstall" is a little ambiguous without more details, sorry.  Your dual boot suggests that you installed ubuntu and kubuntu to separate disk partitions.  Are you trying to not see the kubuntu option any more, put something else on that partition, or do you want to expand the ubuntu install to also use the space occupied by kubuntu?  Could you show us the output of ```
sudo fdisk -l; sudo blkid; cat /etc/fstab
```

Note that it is ok to install the "kubuntu4-desktop" package on top of an existing ubuntu install, or "ubuntu-desktop" on top of kubuntu.  These are not mutually exclusive choices.  You do have to pick whether you want "gdm" (gnome, ubuntu) or "kdm" (KDE, kubunut) to be the login and display manager.  But either way you can have both sets of applications available.

---

