---
title: "How do I remove a broken package?"
date: 2013-09-18
forum: Installation &amp; Upgrades
---

### Post by helasraizam on 2013-09-18
emacs-snapshot from Cassou's repository is broken on my system.  When I try to sudo apt-get autoremove/clean/update/upgrade/install/remove, all halt with an error pertaining to the broken package.  sudo dpkg -install -f and sudo apt-get --configure -a don't work either, and neither do any of these operations in synaptic ('fix broken packages' included).  The error, common to any of these that will output it, is 'Byte compilation for emacs-snapshot failed.'

I can't upgrade or install anything because this package is locking up my system.

---

### Post by Frogs Hair on 2013-09-18
You need to insert correct package name at the end each of these commands. Check your software and  update sources if you use the second command successfully. 

```
sudo dpkg --remove --force-remove-reinstreq package name here
```

```
sudo dpkg --remove -force --force-remove-reinstreqgrep ^ /etc/apt/sources.list /etc/apt/sources.list.d/* package name here
```

---

### Post by helasraizam on 2013-09-18
The first command failed (I didn't try the second line in case these needed to be executed in order)--here is the raw terminal output:

helasraizam@Hela:~$ sudo dpkg --remove --force-remove-reinstreq emacs-snapshot
[sudo] password for helasraizam: 
Sorry, try again.
[sudo] password for helasraizam: 
Sorry, try again.
[sudo] password for helasraizam: 
(Reading database ... 1326398 files and directories currently installed.)
Removing emacs-snapshot ...
Cleaning up add-on packages... failed.

!! emacs-remove emacs-snapshot failed!
!! Please file a bug report against emacs-snapshot
!! and attach the file /tmp/emacs-snapshot.H5urio
dpkg: error processing emacs-snapshot (--remove):
 subprocess installed pre-removal script returned error exit status 1
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs-snapshot failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs-snapshot
!! and attach the file /tmp/emacs-snapshot.IJ09vM
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 emacs-snapshot

---

### Post by Frogs Hair on 2013-09-18
They are both force remove commands and the second is not dependent on the first . I have used both.

---

### Post by helasraizam on 2013-09-23
The output of 
```
sudo dpkg --remove -force --force-remove-reinstreqgrep ^ /etc/apt/sources.list /etc/apt/sources.list.d/* emacs-snapshot
```

is

```
dpkg: error: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
```

---

### Post by helasraizam on 2013-10-02
This problem has not been solved, and unfortunately my system is unable to update or install anything at all until the emacs package issue is resolved.  I tried various renditions of the provided code, by the way, without avail (but thanks for the advice!)

So the question still stands, how do I remove this stubborn broken package?  This is an important question, as package management is a core concept of an operating system, and removing a broken package should always, always be possible (especially if it locks apt-get).

---

