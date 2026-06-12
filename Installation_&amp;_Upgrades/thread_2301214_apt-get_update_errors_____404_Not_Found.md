---
title: "apt-get update errors     404 Not Found"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by steven.stegmann on 2015-10-31
I've been using ubuntu and kubuntu since around 2012 and at my present physical location for the last year.

Recently (2 weeks maybe) I've been getting errors when I run "apt-get update".  Here are a couple examples: (48 total errors)[INDENT]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/main Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/restricted Sources
  404  Not Found [IP: 91.189.92.201 80][/INDENT]
Today, all of the errors are showing this same ip address

Since this started apt-get can't find things like emacs, apt-file, meld, or gcc
Here is the terminal session trying to install gcc[INDENT]steve@euler:~$ sudo apt-get install gcc
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gcc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gcc' has no installation candidate
steve@euler:~$ 
[/INDENT]

I'm looking for an explanation and work-around for these and other packages.

Thanks for your help!
Steve

---

### Post by oldos2er on 2015-10-31
Support for Utopic ended last July; the solution is to upgrade or do a clean install of a supported version of Ubuntu.

---

### Post by lisati on 2015-10-31
14.10 (Utopic) reached its use-by date several months ago, and the main software sources for it have been taken off-line. You may want to consider updating to a newer release.

Whichever method of upgrade you choose, don't forget to backup your important data first.

---

### Post by steven.stegmann on 2015-10-31
Thanks!  I wasn't aware of that.
I'll upgrade

---

