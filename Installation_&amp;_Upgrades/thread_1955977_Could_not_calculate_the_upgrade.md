---
title: "Could not calculate the upgrade"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by bull0016 on 2012-04-10
I receive this message when I go to install updates:
[I]Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.[/I]

The updates never appear in the field they usually do. If it has any bearing I run gnome shell on 11.10.

---

### Post by raja.genupula on 2012-04-10
do this in your terminal 

```
sudo apt-get dist-upgrade
```

and try again , :) . 

All the best .

---

### Post by bull0016 on 2012-04-10
Result:
[I]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 gnome-shell : Depends: libmutter0 (< 3.4) but 3.4.0+git20120405.93d06d43-0ubuntu1~11.10~ricotz0 is to be installed
               Depends: gnome-shell-common (= 3.3.4+git20120202.cd30128a-0ubuntu1~11.10~ricotz0) but 3.4.0+git20120404.0a7968a2-0ubuntu1~11.10~ricotz0 is to be installed
               Recommends: gnome-session-fallback but it is not going to be installed
 libmutter0 : Breaks: gnome-shell (< 3.3.92~) but 3.3.4+git20120202.cd30128a-0ubuntu1~11.10~ricotz0 is to be installed
 mutter-common : Breaks: gnome-shell (< 3.3.92~) but 3.3.4+git20120202.cd30128a-0ubuntu1~11.10~ricotz0 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.[/I]

Hopefully that helps

---

### Post by raja.genupula on 2012-04-10
```
sudo apt-get install -f
```

---

### Post by bull0016 on 2012-04-10
Result:
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 180 not upgraded.
[/I]

---

### Post by raja.genupula on 2012-04-10
[http://www.linuxforums.org/forum/debian-linux/59318-package-problem-broken-dependency-more.html](http://www.linuxforums.org/forum/debian-linux/59318-package-problem-broken-dependency-more.html)

look at post #6

---

### Post by bull0016 on 2012-04-10
Still didn't work
Think I might have to do fresh install, which sucks ****

---

