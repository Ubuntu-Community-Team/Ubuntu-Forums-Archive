---
title: "completely removing software"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by rob1984 on 2007-11-29
hi

i've recently installed deluge torrent client. it worked once and now won't open.

i want to completely remove the program so i can re-install it, the problem is that it doesnt appear in the add/remove window.

how do i use the shell to completely remove the program and revert any changes?

cheers

[edit]
i've just realised that azureus won't open either.  does anybody know what's wrong?

---

### Post by logos34 on 2007-11-29
sudo apt-get remove --purge deluge-torrent

(removes pkg AND config files)

However, you might try fixing them first with:

sudo apt-get install -f

sudo dpkg --configure -a

---

### Post by rob1984 on 2007-11-29
ok thanks a lot!

so i can try to help myself in the future just a couple of questions-

will the apt-get remove command work the same for any program?
does the install -f  attempt to fix all packages?
what's dpkg?

cheers

---

### Post by logos34 on 2007-11-29
it'll work for any installed .deb pkg, not for software compiled from source. (unless you used auto-apt & checkinstall).

[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)
[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

---

### Post by rob1984 on 2007-11-29
cheers!

---

