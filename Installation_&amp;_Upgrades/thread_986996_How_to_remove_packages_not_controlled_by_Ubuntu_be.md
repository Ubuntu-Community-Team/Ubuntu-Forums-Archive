---
title: "How to remove packages not controlled by Ubuntu before network upgrade to 8.10?"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by jis on 2008-11-19
In [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) it is told that "Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade." So how do you get rid of such packages?

---

### Post by Partyboi2 on 2008-11-19
Open up Software Sources (Applications>System>Software Sources) then on the 3rd party tab untick all boxes.

---

### Post by DieB on 2008-11-19
in synaptics you also got these 5 buttons on the bottom left - there is also one that shows u from what source u did get your packages. go through the 3rd parties there and mark the installed for being removed ( do not choose completly remove - due to we want to install them afterwards again). After u selected them all to be removed, go to the menu bar choose file and then "save marked changes under.." give it a name and save it on the desktop.

So now your system should be clean - than go update.


now open your saved file replace the "delete" command after the package-names with "install".
afterwards enable your third parties again, change them if necessary to the proper distribution (hardy, intrepid, ..).  And choose File-load/read saved ... (chosse your file) and it should mark all your formerly installed packages to be installed again.

hope that helps

p.s.: if u cant see your thirds it might be cause u disabled them as noted in the post above.

---

### Post by jis on 2008-11-20
Thanks DieB, but it possible to do it more automatically in command line?

---

### Post by DieB on 2008-11-21
for sure, ig uess it would be done with dpkg (but not sure).

if u want go try out:

> man dpkg

---

### Post by jis on 2008-11-21
There is not much about repositories in man pages of aptitude, apt-get and dpkg (the first output looks odd btw):
> $ man aptitude | grep repositor
<standard input>:410: warning: `deb' not defined (probable missing space after `de')
<standard input>:436: warning: `deb' not defined (probable missing space after `de')
$ man apt-get | grep repositor
           clean clears out the local repository of retrieved package files.
           Like clean, autoclean clears out the local repository of retrieved
$ man dpkg | grep repositor


---

### Post by DieB on 2008-11-23
well with lookin into man dpkg i found:

> dpkg --get-selections >myStatus

which creates the list, u later could use to reinstall your packages via synaptic (or dselect as mentioned in man dpkg).

---

