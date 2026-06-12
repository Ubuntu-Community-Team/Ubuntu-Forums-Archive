---
title: "Needs to be reinstalled, but cannot find an archive"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by Dimitar Uzunov on 2007-04-26
Hello! I've just installed Ubuntu on my R60e Thinkpad and it detected my hardware perfectly and installed the proper drivers, but unfortunately I interrupted the installation of virtualbox and now I can't install or remove anything. I get this when I use any of the package installation programs:
> Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'
I tried "sudo apt-get remove virtualbox" but it gave the same error message. I will appreciate any suggestions you give me.
Thanks for your attention.

---

### Post by mkaylor on 2007-04-26
Same Problem

---

### Post by zvacet on 2007-04-27
```
 sudo apt-get remove --purge file_name
```

---

### Post by Dimitar Uzunov on 2007-04-27
I've already tried - I get this:
> 
dimitar@dimitar-laptop:~$  sudo apt-get remove --purge virtualbox
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.


---

### Post by Dimitar Uzunov on 2007-04-27
I found the solution thanks to mkaylor:
[http://ubuntuforums.org/showthread.php?t=424665](http://ubuntuforums.org/showthread.php?t=424665)
> 
sudo dpkg --remove --force-remove-reinstreq virtualbox
this line removes virtualbox

---

### Post by sambehera on 2008-01-08
thanks.... this fixed my problem as well... except i had a problem with intel's alsa-driver package instead of virtualbox

---

