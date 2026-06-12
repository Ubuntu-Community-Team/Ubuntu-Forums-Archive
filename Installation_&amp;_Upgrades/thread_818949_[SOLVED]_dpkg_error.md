---
title: "[SOLVED] dpkg error"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by swoll1980 on 2008-06-04
When I try to install anything it works, but I get this error:
 
install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up icedtea-gcjwebplugin (1.0-0ubuntu6) ...
update-alternatives: unable to make /usr/lib/firefox/plugins/libjavaplugin.so.dpkg-tmp a symlink to /etc/alternatives/firefox-javaplugin.so: No such file or directory
dpkg: error processing icedtea-gcjwebplugin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea-gcjwebplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't even want icedtea I don't know how this happend. Can someone help me out please?

---

### Post by iaculallad on 2008-06-04
Had you tried running if it corrects your error:

```
sudo dpkg --configure -a
```

---

### Post by swoll1980 on 2008-06-04
> **iaculallad said:**
> Had you tried running if it corrects your error:

```
sudo dpkg --configure -a
```

:~$ sudo dpkg --configure -a
[sudo] password for nolan: 
Setting up icedtea-gcjwebplugin (1.0-0ubuntu6) ...
update-alternatives: unable to make /usr/lib/firefox/plugins/libjavaplugin.so.dpkg-tmp a symlink to /etc/alternatives/firefox-javaplugin.so: No such file or directory
dpkg: error processing icedtea-gcjwebplugin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea-gcjwebplugin

---

### Post by iaculallad on 2008-06-04
This works with Gutsy and I don't know if it will too with Hardy. Try following up with this [post]("http://ubuntuforums.org/showthread.php?t=580792&page=10") and use post #7 if it will fix your icetea problem:

---

### Post by swoll1980 on 2008-06-04
> **iaculallad said:**
> This works with Gutsy and I don't know if it will too with Hardy. Try following up with this [post]("http://ubuntuforums.org/showthread.php?t=580792&page=10") and use post #7 if it will fix your icetea problem:

It's all fixed now

---

