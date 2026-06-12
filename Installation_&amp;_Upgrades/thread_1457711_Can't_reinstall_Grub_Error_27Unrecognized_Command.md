---
title: "Can't reinstall Grub Error 27:Unrecognized Command"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by Arwen17evenstar on 2010-04-19
I have Ubuntu Karmic 9.10 installed, but it was an upgrade so it's still using Grub Legacy. I've done what I've always done in the past.

"sudo grub
root(hd0,1)
setup (hd0)"

It enters grub fine, but when I type in "root(hd0,1)"
It replies "Error 27: Unrecognized Command"
WTF?

I've tried twice now reloading it from the live cd.

Please help!

I'd be happy to install grub2 or whatever I need to do to get my bootloader back without completely reinstalling the OS.

P.S. I KNOW grub is installed on (hd0,1) so that is not the problem.

---

### Post by Arwen17evenstar on 2010-04-19
bump

---

### Post by anasofiapaixao on 2011-01-13
I've just had this problem. Turns out the issue was... *not putting a space between 'root' and '(hd0,1)'*. Yeah, exactly ](*,).

Try writing 'root (hd0,1)' instead of 'root(hd0,1)'.

---

