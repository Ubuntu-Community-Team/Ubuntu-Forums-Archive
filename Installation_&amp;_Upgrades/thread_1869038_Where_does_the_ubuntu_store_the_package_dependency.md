---
title: "Where does the ubuntu store the package dependency information"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by princemaozh on 2011-10-25
1) First trial:
At the beginning, my workstation is online, and I installed some packages using command "sudo apptitude install ...". (but I did NOT install vim-gnome)
 
Later my workstation becomes offline (without internet access), i typed the below command:
 
[HTML] 
maoz@maoz-ws:~$ sudo aptitude install vim-gnome
[/HTML] 
and it says:
[HTML] 
The following NEW packages will be installed:
libreadline5{a} libruby1.8{a} vim-gnome vim-gui-common{a} vim-runtime{a} 
0 packages upgraded, 5 newly installed, 0 to remove and 350 not upgraded.
Need to get 8,716kB of archives. After unpacking 35.5MB will be used.
Do you want to continue? [Y/n/?]
[/HTML] 
the machine is offline and I did not install vim-gnome before. i am just wondering **how aptitude knows the dependencies** for vim-gnome?
 
2) second trial:
on an offline machine which is never online, i typed the same command:
[HTML] 
maoz@maoz-ws2:~$ sudo aptitude install vim-gnome
[/HTML] 
but it says:
[HTML] 
Couldn't find any package whose name or description matched "vim-gnome"
Couldn't find any package whose name or description matched "vim-gnome"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[/HTML] 
 
**So, why it behaves differently in these 2 cases? What is the trick?**
**Where (in which files) does the ubuntu store the package dependency information etc?**

---

### Post by dino99 on 2011-10-25
you can list them all for each package when using synaptic for example

---

### Post by Toz on 2011-10-25
> **princemaozh said:**
> 
So, why it behaves differently in these 2 cases? What is the trick?
Perhaps the apt cache was never updated on the second machine after install?
> Where (in which files) does the ubuntu store the package dependency information etc?
You can use "apt-cache depends" and "apt-cache rdepends" to get dependency information. For example:
```
toz@oneiricX:/var/cache$ apt-cache policy vim-gnome
vim-gnome:
  Installed: (none)
  Candidate: 2:7.3.154+hg~74503f6ee649-2ubuntu3
  Version table:
     2:7.3.154+hg~74503f6ee649-2ubuntu3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages
toz@oneiricX:/var/cache$ apt-cache depends vim-gnome
vim-gnome
  Depends: vim-gui-common
  Depends: vim-common
  Depends: vim-runtime
  Depends: libacl1
  Depends: libbonoboui2-0
  Depends: libc6
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgnome2-0
  Depends: libgnomeui-0
  Depends: libgpm2
  Depends: libgtk2.0-0
  Depends: libice6
  Depends: liblua5.1-0
  Depends: libpango1.0-0
  Depends: libperl5.12
  Depends: libpython2.7
  Depends: libruby1.8
  Depends: libselinux1
  Depends: libsm6
  Depends: libtinfo5
  Depends: libx11-6
  Depends: libxt6
  Depends: tcl8.5
  Suggests: cscope
  Suggests: vim-doc
  Suggests: ttf-dejavu
  Suggests: gnome-icon-theme
toz@oneiricX:/var/cache$ apt-cache rdepends vim-gnome
vim-gnome
Reverse Depends:
 |vimhelp-de
 |vimhelp-de
  vim-rails
  gtimelog
 |vim-runtime
 |vim-gui-common
 |vim-dbg
 |vim-common

```

---

### Post by princemaozh on 2011-10-26
thanks for your reply, Toz.
 
> Perhaps the apt cache was never updated on the second machine after install?

is there any way to update the apt cache on a offline machine?
 
> You can use "apt-cache depends" and "apt-cache rdepends" to get dependency information. For example:

I want to know which file(s) actually store the package/dependency information... so that I can hack the file(s) on the offline machine. and therefore, the offline installation can proceed.
 
Anybody has ideas?

---

### Post by Toz on 2011-10-26
There are tools available that allow you to update offline machines. See: [https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection]("https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection")

---

