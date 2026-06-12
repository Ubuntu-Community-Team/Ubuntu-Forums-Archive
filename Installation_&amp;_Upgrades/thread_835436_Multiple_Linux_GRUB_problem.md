---
title: "Multiple Linux GRUB problem"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by Tony0945 on 2008-06-20
A friend asked me to install Linux on his computer. I installed Fedora Core 2, Fedora Core 5, and Ubuntu Dapper Drake. The computer is an old K6-2 with a serial mouse. That's why I installed older linux versions, for the i586 and serial mouse support.

The GRUB is unlike any that I've ever installed. It lists the UBUNTU options fine, but messes up the Fedora options. I've edited menu.lst, but it keeps offering four Fedora options instead of two, and when I select the boot entry for the Fedora Core 5 on the correct partition, it tries (and fails of course) to boot a gentoo kernel that no longer exists. I've tried running update-grub as root several times as well as editing menu.lst to remove spurious entries. I've also tried locking and unlocking alternatives.

Can anyone point me to a HOW-TO on this strange version of grub? I've also tried "apt-get grub2" but grub2 couldn't be found.

For reference, I am experienced with Caldera, RedHat and derivatives, and Gentoo, but have never worked with a Debian based system before. One option is to re-install as Ubuntu only, but I wanted my friend to sample different distro's. Originally, I was going to install, Fedora, Gentoo, and Ubuntu but after four days of compiling, the Gentoo X11 system still didn't work.

---

### Post by Pumalite on 2008-06-20
Maybe this link might help:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

