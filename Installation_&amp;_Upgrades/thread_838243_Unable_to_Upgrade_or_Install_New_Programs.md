---
title: "Unable to Upgrade or Install New Programs"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by Tuckerfan on 2008-06-23
I had to rebuild my machine (an ancient 750 Mhz AMD box with about half a gig of RAM) and used the Dapper CD I had handy, figuring once I got it installed, I could update the machine to something newer.  The machine locked up during the updating and I had to reboot it.  When I logged in and tried to resume the process I got error messages or the various apps I used to try and install the upgrades (or new programs) would promptly crash.  The error messages I'm getting are:

> A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong.  The error message was: 'Error: Opening the cache (E: Problem parsing dependency Depends, E:Error occurred while processing sound-juicer (NewVersion1). E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.)'

So how do I fix all of this?  Package manager will run, but I can't figure out to find and correct the problems with it, terminal will open, but I don't know the necessary commands to correct the problem.  Update Manager will launch and then promptly crash.  I've tried to install individual programs via package manager, but that doesn't work.

---

### Post by Midwest-Linux on 2008-06-23
Try typing this in the terminal.


sudo dpkg --configure -a

---

### Post by Tuckerfan on 2008-06-23
Did that and got the following response:> dpkg: parse error, in file `/var/lib/dpkg/status' near line 6185 package `sound-juicer':
 `Depends' field, missing package name, or garbage where package name expected


---

### Post by Midwest-Linux on 2008-06-23
> **Tuckerfan said:**
> Did that and got the following response:

 The only thing I could suggest from here is to do a fresh install with a newer distro. I'm sorry I can't help more.

---

### Post by bapoumba on 2008-06-23
Which version of ubuntu are you running now ?
The description for sound-juicer is corrupt in /var/lib/dpkg/status. You can try to fix it by manually editing the file to add back the proper dependencies (back it up first).

> **Tuckerfan said:**
> Did that and got the following response:
> dpkg: parse error, in file `/var/lib/dpkg/status' near line 6185 package `sound-juicer':
`Depends' field, missing package name, or garbage where package name expected 


---

### Post by Tuckerfan on 2008-06-23
I'm running Dapper Drake.  How do I manually edit the file?

---

### Post by bapoumba on 2008-06-23
Here are the dependencies for sound-juicer : [http://packages.ubuntu.com/dapper/sound-juicer]("http://packages.ubuntu.com/dapper/sound-juicer").

Could you please open /var/lib/dpkg/status and look for the description for sound-juicer dependencies. Please paste this part in here, so we can have a look.

Here is mine (not suitable to you, this is the hardy version):
```
Package: sound-juicer
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 4872
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Version: 2.22.0-1ubuntu2
Depends: [COLOR="Red"]<-- here is where yours should be corrupt[/COLOR] 
```

---

