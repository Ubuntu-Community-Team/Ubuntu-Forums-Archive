---
title: "&quot;Could not mark all packagesfor installation or upgrade.&quot;"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by underworld288 on 2008-09-16
Why when I trying to install pretty much anything synaptic gives me this error? I have all of the repos checked (main, restricted, universe, multi universe). The package I'm trying to install right now is the dev files to GTK+ 2. When I click to install the files it gives me this... (see attached screenshot). Well anyway, does anyone know what could be the problem?

---

### Post by iaculallad on 2008-09-16
Input the terminal command below and post whatever error/message it displays:

```
sudo dpkg --configure -a
```

---

### Post by underworld288 on 2008-09-16
Acually, it didn't output anything.

---

### Post by iaculallad on 2008-09-16
Try installing the libgtk2.-dev package:

```
sudo apt-get install libgtk2.0-dev
```

---

### Post by underworld288 on 2008-09-16
```
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
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.12.9-3ubuntu4) but 2.12.9-4ubuntu3 is to be installed
E: Broken packages

```

---

### Post by underworld288 on 2008-09-18
bump. c'mon somebody has to know how to fix this.

---

### Post by underworld288 on 2008-09-18
ok, well looking around the forum I found [this]("http://ubuntuforums.org/showthread.php?p=5479987") thread. Well I followed the directions on how to fix it but when I go to force my version of libgtk2.0 to 2.19.9-4ubuntu3 it says I have to uninstall the ubuntu-desktop. How would I not uninstall the ubuntu-desktop while forcing the right version of libgtk?

---

### Post by underworld288 on 2008-09-18
Nevermind, I didn't think it was safe to uninstall the ubuntu-desktop package. But I see that as long as you reinstall it it's ok.

---

### Post by Sef on 2008-09-18
> Nevermind, I didn't think it was safe to uninstall the ubuntu-desktop package. But I see that as long as you reinstall it it's ok.

Has that fixed your problem?

---

### Post by underworld288 on 2008-09-19
Yea, that fixed it.

---

### Post by syanideatresillience on 2012-04-28
You're in luck, because I have found the solution!

It would seem that you have broken packages, or packages installed that are no longer needed.  You can fix this error message by terminal (as root):

```
apt-get autoremove
apt-get update
apt-get install (whatever package you were trying to install)
```

This fixed this for me, and I was able to proceed.

Cheers!

---

