---
title: "Nessus"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by habadaba on 2005-06-24
When trying to install nessus i get the following :

root@habadaba:/home/pvd # sh nessus-installer-2\[1\].2.4.sh
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
The command 'gtk-config' was not found in your $PATH.

I had a look thru synaptic and all the gtk stuff is install including the libgtk stuff.

Any ideas? I'm close to the point of formatting and installing Mandrake! 

 ](*,)

---

### Post by fdoving on 2005-06-24
[QUOTE=habadaba]When trying to install nessus i get the following :

root@habadaba:/home/pvd # sh nessus-installer-2\[1\].2.4.sh
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
The command 'gtk-config' was not found in your $PATH.

I had a look thru synaptic and all the gtk stuff is install including the libgtk stuff.

Any ideas? I'm close to the point of formatting and installing Mandrake! 

 ](*,)[/QUOTE]
 Hi.

I'd recommend adding universe to your apt-sources [http://ubuntulinux.org/#extrarepositories](http://ubuntulinux.org/#extrarepositories)

And then install nessus from Synaptic


Anyway ,if you still want to compile it your self, you can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and do a content search for 'gtk+-2.0.pc'. This will give you a package name, install the package from Synaptic, and try to run the installer again.

I recommend doing it the 'Ubuntu-way', installing nessus from synaptic.

---

