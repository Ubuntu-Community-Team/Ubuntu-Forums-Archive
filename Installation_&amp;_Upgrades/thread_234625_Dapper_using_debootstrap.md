---
title: "Dapper using debootstrap"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by DougZ on 2006-08-11
Does anyone know of a guide to installing Dapper using debootstrap that ACTUALLY WORKS?

2 weeks in and still cant install. No wonder Bill Gates is so rich...

---

### Post by mlind on 2006-08-11
Tried reading debootstrap manual page (man debootstrap) ? It includes nice HOWTO for sid, just replace distribution with **dapper**.
You'll need [dapper's debootstrap package]("http://archive.ubuntu.com/ubuntu/pool/main/d/debootstrap/debootstrap_0.3.3.0ubuntu2_all.deb")

```

sudo debootstrap dapper /path/to/dapper-root http://archive.ubuntu.com/ubuntu

```

---

### Post by DougZ on 2006-08-15
Nice. Now do you have instructions readable by humans? ](*,) 

Ironically there are guides on how to install Dapper into gentoo and a bunch of others that just don't quite work under Edge. And I don't have the experience to adapt it.

Every six months or so I try, really try, to make linux work for me. In the end I wind up scrapping it after a couple weeks of sheer frustration.

Sidenote: Every *nix developer on the planet should read these two posts. Finally someone (from the *nix community) tells it like it really is.

[http://www.catb.org/~esr/writings/cups-horror.html](http://www.catb.org/~esr/writings/cups-horror.html)

And from the user's point of view, and is actually about Unbuntu in particular:

[http://www.newhorizonssucks.net/LiveCD.html](http://www.newhorizonssucks.net/LiveCD.html)

---

### Post by mlind on 2006-08-15
> **DougZ said:**
> Nice. Now do you have instructions readable by humans? ](*,) 

Ironically there are guides on how to install Dapper into gentoo and a bunch of others that just don't quite work under Edge. And I don't have the experience to adapt it.

Every six months or so I try, really try, to make linux work for me. In the end I wind up scrapping it after a couple weeks of sheer frustration.

Sidenote: Every *nix developer on the planet should read these two posts. Finally someone (from the *nix community) tells it like it really is.

[http://www.catb.org/~esr/writings/cups-horror.html](http://www.catb.org/~esr/writings/cups-horror.html)

And from the user's point of view, and is actually about Unbuntu in particular:

[http://www.newhorizonssucks.net/LiveCD.html](http://www.newhorizonssucks.net/LiveCD.html)

How detailed instructions do you want? I'm a newbie myself and I was able to get running system by using those instructions.

There's a thread about debbootstrapping Edgy, which taken from debootsrap manual example [http://www.ubuntuforums.org/showthread.php?t=205322](http://www.ubuntuforums.org/showthread.php?t=205322)

After debootrapping Dapper, copy /etc/hosts and /etc/sudoers to chroot. Then I guess you should install ubuntu-base, ubuntu-minimal, ubuntu-standard (and maybe ubuntu-desktop) packages.

Use adduser as root to create new user, and assign it to **admin** group. Then use aptitude/apt-get to install kernel and grub if you want to be able to boot in this system.

---

### Post by DougZ on 2006-08-16
My apologies. That is actually quite clear.

Being thoroughly cross-eyed, and a wee bit short of temper, at that point I could HAVE SWORN the post said "check out the man page for debootstrap" - Hence the "got something readable by humans" comment.

I'm just not getting how to put it all together and boot to the new install, then wipe edgy off. Gonna mess around a see just how badly I can screw it up.

---

