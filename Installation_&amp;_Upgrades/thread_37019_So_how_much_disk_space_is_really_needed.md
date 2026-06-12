---
title: "So how much disk space is really needed?"
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by p.n on 2005-05-25
I have a 2.1GB disk on an old Pentium 200MHz machine.  Obviously the install took quite some time but close to the end I got an error message that I might not have enough disk space. The CD however claims that 1.8GB should be enough for a full install.

Is it possible to do a custom install and leave some of the stuff off such as OpenOffice?

Regards
p.n

---

### Post by jkndrkn on 2005-05-25
[QUOTE=p.n]Is it possible to do a custom install and leave some of the stuff off such as OpenOffice?n[/QUOTE]

Not sure, but it *is*  possible to remove a bunch of stuff after the install is complete. You might even want to remove much of gnome, since it is likely to run slow on your box.

Contemplate a switch to xfce (easy) or fluxbox (trickier).

---

### Post by Fab on 2005-05-25
[QUOTE=p.n]I have a 2.1GB disk on an old Pentium 200MHz machine.  Obviously the install took quite some time but close to the end I got an error message that I might not have enough disk space. The CD however claims that 1.8GB should be enough for a full install.

Is it possible to do a custom install and leave some of the stuff off such as OpenOffice?

Regards
p.n[/QUOTE]
 i suggest typing "server" at the boot prompt (without the ") and then install what you need instead of deleting what you dont need

---

### Post by clb137 on 2005-05-25
[QUOTE=p.n]I have a 2.1GB disk on an old Pentium 200MHz machine.  Obviously the install took quite some time but close to the end I got an error message that I might not have enough disk space. The CD however claims that 1.8GB should be enough for a full instal.

Is it possible to do a custom install and leave some of the stuff off such as OpenOffice?

Regards
p.n[/QUOTE]


Have you tried Horay????


the later version


clinton

---

### Post by p.n on 2005-05-25
[QUOTE=clb137]Have you tried Horay????


the later version


clinton[/QUOTE]

Hoary won't install at all...

---

### Post by clb137 on 2005-05-27
[QUOTE=p.n]Hoary won't install at all...[/QUOTE]

can you give me the exact errors?


clinton

---

### Post by az on 2005-05-27
You need 1.8 gigs of filesystem space, which is a little bit more than 2.1 gigs of raw disk space.  The installer is also creating a (needed) swap space which varies in size, depending on how much ram you have installed.

The installer loads up your apt cache with uninstalled packages from the cd.  You can avoid that by installing with the
archive-copier/copy=flase
argument to your install

Type
linux archive-copier/copy=flase
at the prompt when you install.  That saves you about 300 megs of disk space and should avoid all your problems.

They should list that option on the help screens!

Try installing Hoary like this...

---

### Post by p.n on 2005-05-28
I eventually managed to get Warty installed by doing a custom install and then an apt-get ubuntu-desktop.  I still took some serious effort and did not go smoothly but I managed to get it going.  X and all.

> 
Quote:
Originally Posted by p.n
Hoary won't install at all...


can you give me the exact errors?

Difficult to say what exactly the problem with the Haory install is.  It gets to the pont of starting system logger: syslogd, klogd and then keeps giving me 
```

device '/dev/vc/1' does not exist
device '/dev/vc/3' does not exist
device '/dev/vc/4' does not exist
device '/dev/vc/2' does not exist
```

and this is repeated ad infinitum...

So.  I got Ubuntu (Warty) running but, problem is, a Pentium 200 with 96MB RAM and a 2.1 GB hard drive just doesn't cut it...

Slow as hell.

But thanks anyway.

p.n

---

