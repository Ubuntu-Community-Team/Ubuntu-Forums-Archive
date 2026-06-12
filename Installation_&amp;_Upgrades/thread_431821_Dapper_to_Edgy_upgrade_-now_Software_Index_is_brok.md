---
title: "Dapper to Edgy upgrade -now Software Index is broken error"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by rainchild on 2007-05-03
I am getting this error when I try to use the update manager, synaptic tells me I have 25 broken packages but everything I tried to do using synaptic failed
[I]
"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first[/I]."

When I run   "sudo apt-get install -f" I get this error below ( I pasted the tail of the error message)

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 5701 package `gnome-pilot-conduits':
 `Depends' field, reference to `libgnome-pilot2': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)


Any help appreciated!!!!

---

