---
title: "apt crapped up again"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by nihilocrat on 2005-11-22
I tried doing a dist-upgrade in Kubuntu from hoary to breezy, following the instructions, and this is something that happened along the way...

After part of the upgrade process was complete it died and complained. This is what happened when I tried typing 'apt-get dist-upgrade' again.
```

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  python-wxgtk2.6: Depends: python-wxversion but it is not installed
E: Unmet dependencies. Try using -f.

```

This is what happens when I run 'apt-get -f install'

```

Preconfiguring packages ...
(Reading database ... 87233 files and directories currently installed.)
Unpacking python-wxversion (from .../python-wxversion_2.6.1.1.1ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/python-wxversion_2.6.1.1.1ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/wxversion.py', which is also in package wxpython2.5.3
Errors were encountered while processing:
 /var/cache/apt/archives/python-wxversion_2.6.1.1.1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've already done 'apt-get clean' to re-download the package, but it keeps having the same problem. Neither of the packages it is talking about are installed according to apt, but wxversion.py exists.

I don't have much experience fixing apt when it royally screws up like this, any suggestions?

---

### Post by darth_vector on 2005-11-22
an 

apt-cache search python-wxversion 

shows that its in the repositories. maybe you have an incomplete repository list. have a look at:

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

that should fix your problems.

---

### Post by nihilocrat on 2005-11-22
Sorry if the post above seems a little hasty, I was really alarmed because mysql, xinetd, and some other important services stopped working.

I got around the problem by telling apt to ignore those packages with dselect, but thanks anyways. My sources seem fine, and 'apt-get update' works properly. It would be nice to know if there are any other ways to try to fix the problem, though, for future reference and for if I ever really really want those packages (I sometimes develop apps in wxPython, but usually on a different box).

---

