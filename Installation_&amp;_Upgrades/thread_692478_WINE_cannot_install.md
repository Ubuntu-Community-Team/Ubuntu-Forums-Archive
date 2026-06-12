---
title: "WINE cannot install"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by sior9842 on 2008-02-09
I have been trying to install wine so I can emulate a windows program.  I did a little bit of digging, and I found a website detailing the install.  I got to where I should apt-get install wine, but this is what happened:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages



Can anyone help me?  D:

---

### Post by Pumalite on 2008-02-09
Post the output of:
sudo apt-get install -f

---

