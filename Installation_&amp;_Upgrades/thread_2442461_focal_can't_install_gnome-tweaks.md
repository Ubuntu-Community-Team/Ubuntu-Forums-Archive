---
title: "focal: can't install gnome-tweaks"
date: 2020-05-04
forum: Installation &amp; Upgrades
---

### Post by VMC on 2020-05-04
I zsync'ed todays ISO 05032020. Apparently there's a new shell ( 3.36.1-5ubuntu2). Read below why I can't install tweaks:

```
sudo aptitude install gnome-tweaks
The following NEW packages will be installed:
  gir1.2-handy-0.0{a} gnome-shell-extension-prefs{ab} gnome-tweaks 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 74.1 kB of archives. After unpacking 541 kB will be used.
The following packages have unmet dependencies:
 gnome-shell-extension-prefs : Depends: gnome-shell (= 3.36.1-5ubuntu1) but 3.36.1-5ubuntu2 is installed
                               Depends: gnome-shell-common (= 3.36.1-5ubuntu1) but 3.36.1-5ubuntu2 is installed
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell-extension-prefs [Not Installed]        
2)     gnome-tweaks [Not Installed]
```

Is the **released** Focal really have gnome-shell 3.36.1-5ubuntu1 ?

---

### Post by Dennis N on 2020-05-04
> Is the released Focal really have gnome-shell 3.36.1-5ubuntu1 ? 
Yes.
```
dmn@Tyana-vm:~$ gnome-shell --version
GNOME Shell 3.36.1

```

and this gives the package name:
```
dmn@Tyana-vm:~$ apt show gnome-shell
Package: gnome-shell
Version: 3.36.1-5ubuntu1
```

---

### Post by VMC on 2020-05-04
Thanks. Now look at the current Focal:

```
$ apt show gnome-shell
Package: gnome-shell
Version: **3.36.1-5ubuntu2**
```

Then:

```
$ gnome-shell --version
GNOME **Shell 3.36.1**
```

The newest shell won't work with tweaks.

edit:i placed an issue at git see if they respond.

---

### Post by ActionParsnip on 2020-05-04
What is the output of:

```

apt-cache policy gnome-shell gnome-shell-common

```

Thanks

---

### Post by VMC on 2020-05-04
```
$ apt-cache policy gnome-shell gnome-shell-common
gnome-shell:
  Installed: **3.36.1-5ubuntu2**
  Candidate: 3.36.1-5ubuntu2
  Version table:
 *** 3.36.1-5ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu focal-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     3.36.1-5ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
gnome-shell-common:
  Installed: 3.36.1-5ubuntu2
  Candidate: 3.36.1-5ubuntu2
  Version table:
 *** 3.36.1-5ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu focal-proposed/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     3.36.1-5ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu focal/main i386 Packages
```

---

