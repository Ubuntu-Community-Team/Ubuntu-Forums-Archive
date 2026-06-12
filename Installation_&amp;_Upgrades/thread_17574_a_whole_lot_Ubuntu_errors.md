---
title: "a whole lot Ubuntu errors"
date: 2005-03-01
forum: Installation &amp; Upgrades
---

### Post by k:arel on 2005-03-01
hi, i'm trying out this Ubuntu Warty Warthog 4.10 from an official cd i got at FOSDEM, Brussels

the installation just refuses to work and i'm getting all sorts of different errors:

while loading the modules from the cdrom, he complains that "No kernel modules were found... This is probably due to a mismatch of the kernel used by this version and the kernel in the one online" and asks if i want to continue the install without them (and "probably the installation won't work")

yet, if i try to load the modules from the Internet he "can't find a file" while downloading, i _do_ have connection with the Internet because i'm getting the listing "stable, testing, unstable" 
(because there isn't a *ping* command, i just tested it with pulling out the cable while retrieving the version listing)
thus, when i choose an ftp/http server, any of them (!), he won't "find a file"
when i change form *stable* to *unstable* in the version listing, i'm getting the previous error "No kernel modules were found ... [blah,blah]"

my cdrom of Ubuntu is fine because when mounting it, it scans all the files without any error

when detecting hardware and loading drivers, he does complain about some *IDE* modules that can't be loaded (but that "isn't a problem because the installer will load them later")

so i'm a little stuck here: i'm using the boot floppy files from the [URL](ftp://ftp.debian.org/debian/dists/unstable/main/installer-i386/current/images/floppy/) given in the install documentation

anybody any idea?

---

### Post by p!=f on 2005-03-01
Stable, testing and unstable are Debian related not Ubuntu ones.

---

### Post by k:arel on 2005-03-01
i forgot this one:
when i choose to "install the base system" (with the wrong kernel module), he pops up this error:
```
Debootstrap Error
Couldn't retrieve dbus-1
This may be a cd-rom or network problem
...
(next screen)
Faild to install the base system
Base system installation into /target/ failed
```
the log output:
```
# cat /var/log/messages | tail
cp: Read error: Input/Output error
```

the weird thing is: he gives this error when installing from the CDrom and when installing (the unstable version) from the Internet

---

### Post by k:arel on 2005-03-01
[QUOTE=p!=f]Stable, testing and unstable are Debian related not Ubuntu ones.[/QUOTE]
then the question is: why would the Ubuntu installer go and fetch the Debian packages?

maybe check my additional post to: i forget a reasionably important error

---

