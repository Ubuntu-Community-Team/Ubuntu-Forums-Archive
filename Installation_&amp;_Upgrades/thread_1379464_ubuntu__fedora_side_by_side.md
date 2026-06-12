---
title: "ubuntu / fedora side by side?"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by trampintransit2 on 2010-01-12
I've got ubuntu already on my desktop, out of interesr i'd like to look at fedora. Whats the best method of installing fedora alongside ubuntu? Shrink the current system or use free space. What the fors and againsts?
ta

---

### Post by ajgreeny on 2010-01-12
I have not looked at Fedora 12, but did try Fedora 11.  It is not good at finding other linux installs so you will probably lose your ability to boot to ubuntu, unless you either edit the Fedora menu.lst, or if it's grub2, run the update-grub command in terminal.

By default Fedora probably still installs in LVM partitions, it certainly used to do so, which can also make life difficult, and can mean it is not straightforward to mount in other linux installs, eg ubuntu.

In spite of many peoples' love of the distro, I'm afraid it did nothing for me other than make life more difficult so I got rid of it fairly quickly.  If you decide to continue, I suggest you manually partition with a more standard partitioning arrangement, use ext4, and probably put grub on the Fedora disk/partition, rather than the MBR, you can then at least continue with the ubuntu grub, and either add Fedora manually or just use update-grub if you already have grub2.

---

### Post by raymondh on 2010-01-12
Just to experiment and see?  

Try virtualbox and virtualize/guest fedora.  When you decide to, you can install fedora anytime in its' own partition.

Just my .02 suggestion :)

Raymond

---

### Post by trampintransit2 on 2010-01-12
can i partition the drive while leaving and not damaging the existing ubuntu installation though? If so, how best to do so?

---

### Post by ajgreeny on 2010-01-13
> **trampintransit2 said:**
> can i partition the drive while leaving and not damaging the existing ubuntu installation though? If so, how best to do so?
Yes easily, using either gparted live CD, or simply the ubuntu live CD which already has gparted in the system- administration menu.

Always backup before doing any partitioning activities, however.

---

