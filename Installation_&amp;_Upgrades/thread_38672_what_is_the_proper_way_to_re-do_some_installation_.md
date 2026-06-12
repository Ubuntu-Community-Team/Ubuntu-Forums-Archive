---
title: "what is the proper way to re-do some installation tasks"
date: 2005-06-01
forum: Installation &amp; Upgrades
---

### Post by fedork on 2005-06-01
I skipped some installation steps because I did not have network connection at that time. What is "The Right Way" to do them after I do get network up and running?

Should I just manually dpkg-reconfigure packages?

---

### Post by Mez on 2005-06-01
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install --reinstall package
```

Replace package witht he package you want to reinstall

---

### Post by fedork on 2005-06-01
that is Ok, but I was referring to the installation script which was doing all the preconfiguration and stuff the installer does.

do I run base-config or something similar?

Also I wandered what to is the "proper" way to install "tasks" s.a. "games" "office" etc as in debian? Do I use tasksel, aptitude/synaptics or is there some special "ubuntu way"?

---

### Post by mingus on 2005-06-01
This really depends on what you skipped.  Most Ubuntu users use apt-get at the command line or Synaptic for a gui alternative, which does the same thing.  All pull from Ubuntu deb repositories.  Apt-get update will reload the package descriptions, and anything needing to be upgraded will be shown in Synpaptic.

On the other hand, if you simply did not install a function, you will need to do that individually depending on what it is.

The wiki documentation is very helpful, as is the following:

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/index.html](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/index.html)

---

### Post by az on 2005-06-01
Ubuntu does not use tasks.  Just install individual packages, really.

Use the netwoking gui for your networking needs.  It does it all.

You can run
sudo base-config
at any time you want...

---

