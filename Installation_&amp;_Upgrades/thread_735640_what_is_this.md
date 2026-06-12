---
title: "what is this???"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by disast1ckup on 2008-03-25
I'm  receiving this message when I try to open the synaptic package manager:
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
what should I do?

---

### Post by steveneddy on 2008-03-25
Open a terminal and type

```

dpkg --configure -a

```

then hit the Enter key.

Tell us what happens next.

---

### Post by disast1ckup on 2008-03-25
now it says "dpkg: requested operation requires superuser privilege"

---

### Post by oldos2er on 2008-03-25
Run "sudo dpkg --configure -a"

---

### Post by steveneddy on 2008-03-25
> **oldos2er said:**
> Run "sudo dpkg --configure -a"

I**[COLOR="Blue"] always[/COLOR]** forget the **sudo** part.

](*,)   <--- dang - that hurts....

---

### Post by disast1ckup on 2008-03-26
now it says:
test@test-laptop:~$ sudo dpkg --configure-a
dpkg: unknown option --configure-a

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by aysiu on 2008-03-26
That's why you copy and paste instead of retyping.

**What you typed**: ```
sudo dpkg --configure-a
``` **What you're supposed to paste in**: ```
sudo dpkg --configure -a
```

---

### Post by prshah on 2008-03-26
> **disast1ckup said:**
> now it says:
test@test-laptop:~$ sudo dpkg --configure-a
dpkg: unknown option --configure-a


You've forgotten the SPACE between --configure and -a

After this, all will be fine.

---

### Post by disast1ckup on 2008-03-26
Great. thank you all, its working. But as a side note  the terminal did say:
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on hal (>= 0.5.10); however:
  Package hal is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured

and also
dpkg: dependency problems prevent configuration of hal-cups-utils:
 hal-cups-utils depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-cups-utils (--configure):
 dependency problems - leaving unconfigured
 how do I configure hal?

---

### Post by WilSteele on 2008-03-26
Been having this same problem in 7.10
I've run the command and this is what i get...

Setting up python-bittorrent (3.4.2-11ubuntu3~7.10) ...

Setting up apturl (0.1ubuntu2) ...

Setting up capplets-data (1:2.20.1-0ubuntu1) ...


... and that's it, It just stays there and never goes further. This problem started when the update manager crashed earlier today. This is a fresh install and the update manager had 204 updates do and crashed after 25.

---

