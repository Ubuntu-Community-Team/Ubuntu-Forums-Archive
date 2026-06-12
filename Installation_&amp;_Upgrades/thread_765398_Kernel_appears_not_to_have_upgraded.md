---
title: "Kernel appears not to have upgraded"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by lolwhites on 2008-04-24
I started discussing my issue [here]("http://ubuntuforums.org/showthread.php?t=764582") until the thread was locked.

Basically I upgraded to Hardy on April 22nd, 2 days before the final release. On booting, the GRUB menu still says:
> Ubuntu 7.10, kernel 2.6.22-14 generic
Ubuntu 7.10, kernel 2.6.22-14 generic (recovery mode)
Ubuntu 7.10, memtest86+
Microsoft Windows XP Home Edition

sudo apt-get update, sudo apt-get dist-upgrade and sudo update-grub make no difference.

lsb_release --short --description yields Ubuntu 8.04.

uname -a gives me this:
> Linux lolwhites-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

So it looks like I've got an old kernel. Any advice?

Edit - the kernel is there, I added an entry to the GRUB menu with QGRUBEditor and it seems to have worked. uname -a now gives:
> Linux lolwhites-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

But I'd rather it did it automatically.

---

