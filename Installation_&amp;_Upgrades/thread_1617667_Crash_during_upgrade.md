---
title: "Crash during upgrade"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by neotifa on 2010-11-09
I went to distro upgrade from karmic to lucid. All the packages were downloaded and it started to install (4 packages made to update). In the same time my pc restarted (with my faulth, an accident). Now when i want to continue with the upgrade process, i get this error:

```
1. Not all updates can be installed
2. Broken packages (
Your system contains broken packages that couldn't be fixed with this software. Please fix them first using synaptic or apt-get before proceeding.)

```
When typed apt-get dist-upgrade in terminal, i receive this:
```
root@stefan-desktop:/home/stefan# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-power-manager: Depends: devicekit-power (>= 011) but it is not installable
  indicator-session: Depends: devicekit-power but it is not installable
  ubuntu-desktop: Depends: usplash but it is not installed
  usplash-theme-ubuntu: Depends: usplash (>= 0.5.30) but it is not installed
E: Unmet dependencies. Try using -f.

```
Also tried apt-get dist-upgrade -f:
```
root@stefan-desktop:/home/stefan# apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  gnome-power-manager: Depends: devicekit-power (>= 011) but it is not installable
  indicator-session: Depends: devicekit-power but it is not installable
  ubuntu-desktop: Depends: usplash but it is not installed
  usplash-theme-ubuntu: Depends: usplash (>= 0.5.30) but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```
How to upgrade the sistem ?

---

### Post by gordintoronto on 2010-11-09
If it were me, I would back up all my data and do a clean install.

---

### Post by sikander3786 on 2010-11-10
You need to resolve the dependency issues before trying the upgrade again. So try

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

If these are successful, try the dist-upgrade again. Otherwise post the output of the above commands.

---

### Post by neotifa on 2010-11-10
> **sikander3786 said:**
> You need to resolve the dependency issues before trying the upgrade again. So try

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```If these are successful, try the dist-upgrade again. Otherwise post the output of the above commands.

Output of apt-get install -f:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  gnome-power-manager: Depends: devicekit-power (>= 011) but it is not installable
  indicator-session: Depends: devicekit-power but it is not installable
  ubuntu-desktop: Depends: usplash but it is not installed
  usplash-theme-ubuntu: Depends: usplash (>= 0.5.30) but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```
dpkg --configure -a:
```
dpkg: error processing libsdl1.2debian (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 libsdl1.2debian

```

---

### Post by sikander3786 on 2010-11-10
Ok try,

```
sudo aptitude reinstall libsdl1.2debian
```

```
sudo aptitude install -f
```

---

### Post by neotifa on 2010-11-10
> **sikander3786 said:**
> Ok try,

```
sudo aptitude reinstall libsdl1.2debian
``````
sudo aptitude install -f
```
The result is little bit ling:
```
http://paste.ubuntu.com/529434/
```

---

### Post by sikander3786 on 2010-11-10
Please see post # 9 in this thread.

[http://ubuntuforums.org/showthread.php?t=1616627](http://ubuntuforums.org/showthread.php?t=1616627)

---

### Post by neotifa on 2010-11-10
Nothing again. But dpkg --configure -a gave this results :
```
dpkg: error processing libsdl1.2debian (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 libsdl1.2debian

```
Is there any way how to install this without the apt-get method ?

---

### Post by TBABill on 2010-11-10
With your system borked the way it is I doubt you will fix it outside of the terminal and going step by step until you resolve the issues. However, you may be able to search Synaptic for each file, as long as Synaptic is working, and search/install each of them as you go through the process. Terminal is much faster if you can just cut/paste what is typed there for you by users helping.

---

