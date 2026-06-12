---
title: "conflict in libgnomekbd4 upgrade"
date: 2009-12-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2009-12-07
```
The following packages will be upgraded:
  libgnomekbd4 
1 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/47.3kB of archives. After unpacking 81.9kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 179529 files and directories currently installed.)
Preparing to replace libgnomekbd4 2.28.0-0ubuntu2 (using .../libgnomekbd4_2.28.0-2ubuntu1_amd64.deb) ...
Unpacking replacement libgnomekbd4 ...
dpkg: error processing /var/cache/apt/archives/libgnomekbd4_2.28.0-2ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libgnomekbdui.so.4.0.0', which is also in package libgnomekbdui4 0:2.28.0-0ubuntu2
Errors were encountered while processing:
 /var/cache/apt/archives/libgnomekbd4_2.28.0-2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

---

### Post by jppr on 2009-12-07
> **zika said:**
> ```
The following packages will be upgraded:
  libgnomekbd4 
1 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/47.3kB of archives. After unpacking 81.9kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 179529 files and directories currently installed.)
Preparing to replace libgnomekbd4 2.28.0-0ubuntu2 (using .../libgnomekbd4_2.28.0-2ubuntu1_amd64.deb) ...
Unpacking replacement libgnomekbd4 ...
dpkg: error processing /var/cache/apt/archives/libgnomekbd4_2.28.0-2ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libgnomekbdui.so.4.0.0', which is also in package libgnomekbdui4 0:2.28.0-0ubuntu2
Errors were encountered while processing:
 /var/cache/apt/archives/libgnomekbd4_2.28.0-2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

[https://launchpad.net/ubuntu/lucid/+source/libgnomekbd/2.28.0-2ubuntu2](https://launchpad.net/ubuntu/lucid/+source/libgnomekbd/2.28.0-2ubuntu2)

e. [http://feeds.ubuntu-nl.org/LucidChanges](http://feeds.ubuntu-nl.org/LucidChanges)

---

### Post by zika on 2009-12-07
> **jppr said:**
> [https://launchpad.net/ubuntu/lucid/+source/libgnomekbd/2.28.0-2ubuntu2](https://launchpad.net/ubuntu/lucid/+source/libgnomekbd/2.28.0-2ubuntu2)

e. [http://feeds.ubuntu-nl.org/LucidChanges](http://feeds.ubuntu-nl.org/LucidChanges)I've seen that annoucement in mail I receive. But, still, I do not get it, where the problem lies, and I still have problem installing it.

---

### Post by zika on 2009-12-08
If I run apitude I get:> $ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
The following packages have been kept back:
  empathy gnome-games 
The following packages will be REMOVED:
  gir1.0-clutter-1.0{u} gir1.0-gconf-2.0{u} gir1.0-gtk-2.0{u} libseed0{u} 
  seed{u} 
0 packages upgraded, 0 newly installed, 5 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 2,220kB will be freed.
Do you want to continue? [Y/n/?] n
Abort.>  sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
The following packages have been kept back:
  empathy gnome-games 
The following packages will be REMOVED:
  gir1.0-clutter-1.0{u} gir1.0-gconf-2.0{u} gir1.0-gtk-2.0{u} libseed0{u} 
  seed{u} 
0 packages upgraded, 0 newly installed, 5 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 2,220kB will be freed.
Do you want to continue? [Y/n/?]
If I remove them, Synaptic wants to install them back ... Apt-get doesn't care.
Who is right?

---

### Post by seeker5528 on 2009-12-10
> **zika said:**
> If I run apitude I get:
If I remove them, Synaptic wants to install them back ... Apt-get doesn't care.
Who is right?

Don't know what's up with Empathy I don't have it installed.

I expect the gir* stuff will work it's self out once the packages that depend on them all get sorted/updated.

Gnome-games seems to be uninstallable at the moment because some games are missing, the name of Same Gnome has been changed to Swell Foop, and the renamed version seems not to be there yet, don't know if all the missing games are the result of name changes or if there are actually some new ones.

Later, Seeker

---

