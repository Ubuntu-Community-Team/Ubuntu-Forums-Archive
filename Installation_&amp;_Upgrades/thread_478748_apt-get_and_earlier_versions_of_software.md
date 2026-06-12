---
title: "apt-get and earlier versions of software"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by WebDrake on 2007-06-19
Suppose that I'm installing from an apt repository which contains more than one version of a piece of software.  By default apt-get will install the one with highest version number.  Is there a way to choose which version to install?

---

### Post by jpeddicord on 2007-06-20
If you are installing from Synaptic, you can select Package > Force Version after selecting one with multiple versions.

If you are installing from apt-get, just specify the exact version number after the package separated with an =. For example:
```
sudo apt-get install thepackage=0.2.4ubuntu2
```

Jacob

---

### Post by mitch.c on 2007-06-20
> **WebDrake said:**
> Suppose that I'm installing from an apt repository which contains more than one version of a piece of software.  By default apt-get will install the one with highest version number.  Is there a way to choose which version to install?
Just tack on the version number:
```
apt-get install foo=1.2.3.4-1
```
Now, this creates a problem in that an 'upgrade' or 'dist-upgrade' will try to upgrade to the latest version. You have two choices.

First, you can 'hold' the package using either of these commands:
```
$ sudo aptitude hold foo
$ sudo bash -c 'echo -e "foo hold" | dpkg --set-selections'
```
Both upgrade and dist-upgrade, as well as the update-manager will constantly tell you you need to update.

Or, you can 'pin' the package by adding something like this to /etc/apt/preferences:
```
Package: foo
Pin: version 1.2.3.4-1
Pin-Priority: 1001
```

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

### Post by HotShotDJ on 2007-06-20
I've used mich.c's third suggestion (editing /etc/apt/preferences) before and it worked perfectly for me.

---

