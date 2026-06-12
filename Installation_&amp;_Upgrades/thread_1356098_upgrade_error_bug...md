---
title: "upgrade error bug.."
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by felixvah on 2009-12-15
does anyone know about this error.. I google it and I didn't find a solution for it. Here's the error..

mcpl@mcpl-laptop:~$ sudo dpkg --configure -a
[sudo] password for mcpl: 
Setting up software-center (1.0.2) ...
file does not exist: /usr/share/software-center/softwarecenter/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/apt/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/db/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/view/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/view/widgets/__init__.py
pycentral: pycentral pkginstall: error byte-compiling files (36)
pycentral pkginstall: error byte-compiling files (36)
dpkg: error processing software-center (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 software-center

I can't install new software, upgrade and etc..
It doesn't matter what I did, i still get these error block:

file does not exist: /usr/share/software-center/softwarecenter/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/apt/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/db/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/view/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/view/widgets/__init__.py

Please help me..

---

### Post by zvacet on 2009-12-15
Try in synaptic mark that package for reinstall and see if it help.

---

### Post by felixvah on 2009-12-16
> **zvacet said:**
> Try in synaptic mark that package for reinstall and see if it help.

it didn't work.

---

### Post by Soul-Sing on 2009-12-16
try: ```
sudo dkpg --configure-a
```

---

### Post by felixvah on 2009-12-16
> **leoquant said:**
> try: ```
sudo dkpg --configure-a
```

I've tried that, no luck!

---

### Post by zvacet on 2009-12-17
When you run 

```
sudo dpkg --configure -a
```

do you get any errors?If you do run command again and post output here.

---

### Post by nibirumarduk on 2009-12-17
felixvah, I have thought of some solutions but I hope you are comfortable working with scripts and perhaps having to do so using cli tools like GNOME Terminal and nano.

The steps:

In GNOME Terminal, type:
sudo nano /var/lib/dpkg/info/software-center.postinst

then
add "exit 0" after set -e (without the quotes)

Save your changes with this key combo:
Ctrl + O

Exit nano with Ctrl + X

Re-run sudo dpkg --configure -a or sudo dpkg --configure --pending; sudo aptitude full-upgrade

See if that works. Otherwise you may need to explore some other options listed below.

General rule of thumb when faced with package script problem of "<package_name>", one should look into following package scripts.

"/var/lib/dpkg/info/<package_name>.preinst"
"/var/lib/dpkg/info/<package_name>.postinst"
"/var/lib/dpkg/info/<package_name>.prerm"
"/var/lib/dpkg/info/<package_name>.postrm"
Edit the offending package script using an editor of your choice e.g. nano and doing so with root/superuser privileges i.e. sudo nano /var/lib/dpkg/info/<package_name>.preinst/postinst/prerm or postrm using following techniques.
1.
disable the offending line by preceding "#"
or
2.
force to return success by appending the offending line with "|| true"
3.
or the easiest option i.e. open up the offending script file i.e. /var/lib/dpkg/info/software-center.postinst in this instance, and append "exit 0" after "set -e"
Configure all partially installed packages with the following command.

Good luck!

---

### Post by felixvah on 2009-12-17
nibirumarduk,

You're too cool.. thanks a lot.. work perfectly by following your instruction.

I got the error message by following some instruction on how to rsync files over a network.  Do you have any resource that would help me too.  I'm trying to rsync files to another Ubuntu box.

Thanks again.

---

