---
title: "Pidgin Problem"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by network.burner on 2008-03-13
**PROB 1** -- [COLOR="Blue"]i tried the .deb package of pidgn for installing
even though i have libpango1.0-0
it says ERROR: DEPENDENCY IS NOT SATISFIABLE: libpango1.0-0[/COLOR]
**PROB 2** -- [COLOR="Blue"]i tried to install with tar.bz2  using make...
while i entered ./configure it gave me an error sayin :[/COLOR]
The msgfmt command is required to build libpurple.  If it is installed
on your system, ensure that it is in your path.  If it is not, install
GNU gettext to continue.

If you have msgfmt installed, but for some reason this error message
is still displayed, you have encountered what appears to be a bug in
third-party configure macros.  Try setting the MSGFMT environment
variable to the absolute path to your msgfmt binary and trying
configure again, like this:

MSGFMT=/path/to/msgfmt ./configure ...
[COLOR="Blue"]when i checked, i found gettext-base installed so i tried to use :[/COLOR]
MSGFMT=/path/to/msgfmt ./configure
[COLOR="Blue"]it gave me another error : [/COLOR]
configure: error:

You must have the GLib 2.0 development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.

[COLOR="Red"][COLOR="Blue"]when i checked synaptic, it showed me libglib2.0-0 installed also pkg-config installed
 I HAD COMPLETELY REMOVED PIDGIN FROM SYNAPTIC BY MISTAKE. PLEASE TELL ME HOW DO I RE INSTALL IT.
ALSO LET ME KNOW WHY THIS ERROR IS OCCURRING 
AND PLEASE EXPLAIN WHY UBUNTU IS ASKING FOR THINGS WHICH ARE ALREADY INSTALLED

[/COLOR][/COLOR]

---

### Post by taurus on 2008-03-13
Any reason you don't want to use the one from the repos?

```
sudo apt-get update
sudo apt-get install pidgin
```

---

### Post by network.burner on 2008-03-14
its ok if i get from any repository.. but how do i get PIDGIN back to my synaptic... cuz i hd removed it completely...
will i get the latest version (2.4.0) from the repO?

---

### Post by network.burner on 2008-03-14
> **taurus said:**
> Any reason you don't want to use the one from the repos?

```
sudo apt-get update
sudo apt-get install pidgin
```

i tried frm the repo.. this is the error its givin me :
[COLOR="Blue"]rahul@rahul-desktop:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pidgin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libpurple0
E: Package pidgin has no installation candidate
[/COLOR]

---

