---
title: "Your advice needed: Ready to ditch te hdual boot"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by DJ_Peng on 2007-11-21
When I first started using Ubuntu, I used a dual boot with WinXP (Home) because there were some apps I needed to use that didn't play well under Wine. With the release of Gutsy I am finally ready to ditch my Windows partition and go 100% Ubuntu (with a few apps running under Wine).

My question is what's the  best way to do this? Should I just unmount the partition, go into Gparted and reformat it as an ext3 drive and start putting that kitty to work as a data partition? I know I'll need to get into  fstab and change how the partition is mounted, but is there anything else I should do?

Just for history's sake, it was just over a year ago that I got fed up with the hassles of being a Windows user and  started looking for the right Linux distro for me. Whodathunk it would be just twelve months later that I'd be ready to send bootable Windows to the great bit bucket in the sky?

---

### Post by aysiu on 2007-11-21
> **DJ_Peng said:**
> Should I just unmount the partition, go into Gparted and reformat it as an ext3 drive and start putting that kitty to work as a data partition? Yes, as long as Ubuntu's Grub is installed to the Master Boot Record (this is the default behavior, unless you manually decided to install Grub elsewhere). That's a good plan.

---

### Post by DJ_Peng on 2007-12-04
I ended up formatting both my former XP partition and my Ubuntu partition and simply reinstalling Ubuntu. It didn't go easily, as I had problems with my Nvidia drivers, but once I got an older version of Envy all was good. Thanks for the assist.

---

