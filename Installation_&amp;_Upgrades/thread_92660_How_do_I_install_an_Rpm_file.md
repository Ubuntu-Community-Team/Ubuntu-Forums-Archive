---
title: "How do I install an Rpm file?"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by bigcanuck on 2005-11-20
I need to install ATI graphics driver for my labtop, but the archive manager in Ubuntu isn't extracting the file, so I was wondering about how do I do that.  Any help is much appreaciated as I'm fairly new to linux.

---

### Post by drummer on 2005-11-20
Ubuntu uses a different package manager called apt, which had .deb packages. rpm packages/files can be converted using this in a terminal:
first install alien with```
sudo apt-get install alien
```then do```
sudo alien file.rpm
``` then installing the .deb with```
sudo dpkg -i file.deb
```
You should also be able to get the ATI drivers from their website as a file "something**.sh**" which can be installed by running from a terminal```
sudo sh something.sh
```without having to convert anything.

---

### Post by Haegin on 2005-11-20
As you may or may not be aware RPMs are linux install files for redhad based distributions. This includes suse, mandrake/mandriva (the old name was soooo much better), redhat, fedora etc. Debian based systems (ubuntu, mepis, debian, etc) all use .deb files to install things.
To install an RPM on a debian based system you can use a program called alien
```

alien --help

```
$ will tell you if you have it or not,
```

$ sudo apt-get install alien

```
will install it if you need it
```

$ sudo alien (options) <name of rpm>

```
will generate a deb package from the rpm.
The options are optional and include things such as -i which automatically installs the generated package. To find out more use ```
man alien
```

I hope this helps

EDIT: Beaten to it, shows how good these forums are!

---

### Post by Arktis on 2005-11-20
[QUOTE=bigcanuck]I need to install ATI graphics driver for my labtop, but the archive manager in Ubuntu isn't extracting the file, so I was wondering about how do I do that.  Any help is much appreaciated as I'm fairly new to linux.[/QUOTE]

Read the various howtos on installing the ati drivers.  You're not supposed to even need an rpm or the manual use of an archive manager; I don't know where you got that idea.

---

