---
title: "Upgrade woes"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Xoanan on 2009-10-10
Hi all

I did that partial upgrade(I know, I shouldn't have) and I am attempting to correct it.

I ran sudo apt-get install -f to correct some reported issues and I found something that might be relevant to the issue

```
One or more running instances of xscreensaver or xlockmore have been detected on this system. Because of incompatible library changes, the upgrade of the GNU libc library will leave you unable to authenticate to these programs. You should arrange for these programs to be restarted or stopped before continuing this upgrade, to avoid locking your users out of their current sessions.

```

and 

```
E: /var/cache/apt/archives/libc6_2.10.1-0ubuntu15_i386.deb: subprocess new pre-installation script returned error exit status 1
```

I don't know if this is a known bug or not. It might just be my system. Any thoughts?
:popcorn:

---

### Post by VMC on 2009-10-10
Have you tried to boot into Recovery(single) Mode and fix it from there?

---

### Post by Xoanan on 2009-10-10
> **VMC said:**
> Have you tried to boot into Recovery(single) Mode and fix it from there?

No, I haven't actually;  I know I can change the bios, but I'm not sure I have a recovery mode per se; this machine has Xubuntu only. There is no Windows partition on it.

---

### Post by lisati on 2009-10-10
> **Xoanan said:**
> No, I haven't actually;  I know I can change the bios, but I'm not sure I have a recovery mode per se; this machine has Xubuntu only. There is no Windows partition on it.
On the grub menu (you might have to press "Esc" to view it), not the BIOS menu, there should be a Xubuntu recovery mode option.

---

### Post by ranch hand on 2009-10-10
If you have grub2 the Esc key will not do it.  You need to hold the space bar down to get the menu up.

No matter if you like a hidden menu normally or not, if you have grub-legacy or grub2, you should change the default in the testing cycle to have the menu visible.

Grub-legacy you do in /boot/grub/menu.lst.

Grub2 you do in /etc/default/grub and run update-grub after that.

---

### Post by Xoanan on 2009-10-11
System crash and I had do a fresh install of 8.04; thanx all

---

