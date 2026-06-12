---
title: "Broken samba Installation"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by venky80 on 2006-07-15
[B]My package manager is showing that my samba installation is broken...i ran synaptics and it shows a red box in front of samba i try to remove it and it shows me an error so i run sudo apt-get install -f and it shows me this
venky@100110-laptop:~$ sudo apt-get install -f[/B]
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 132873 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

**how do i force remove this package?**

---

### Post by nevin on 2006-07-15
im having the same exact problem...
im using a dell inspiron 6000.

---

### Post by Viremia on 2006-07-15
Same here (thinkpad T42)

---

### Post by secundar on 2006-07-15
See this post for the solution...
[http://ubuntuforums.org/showpost.php?p=1249897&postcount=3](http://ubuntuforums.org/showpost.php?p=1249897&postcount=3)

worked for me (Asus z71v, rather messy update from breezy)

---

### Post by nevin on 2006-07-16
worked perfect for me too.
thanks alot.

---

### Post by jamisonaw on 2006-07-16
Exact same here as well. Bad package.

Using a Desktop with a mish-mash of componenets.

---

### Post by clooch on 2006-07-16
worked here too thaank you so much

---

### Post by Moriak on 2006-07-17
I just had this problem.

I found out that a symbolic link was broken for some reason and was the origin of the error:

```
/etc/rc2.d/S91samba 
```

I fixed the link:

```

cd /etc/rc2.d/
rm S91samba
sudo ln -s ../init.d/samba S91samba

```

Reopen synaptic and mark samba for upgrade and everything worked fine.

Hope this help.

Jonathan

---

