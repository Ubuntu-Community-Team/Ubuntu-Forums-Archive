---
title: "build-essential installation in secluded environment (with no Internet)"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by hjqureshi on 2011-08-10
Hi:
 
I have been trying to install build-essential package on Ubuntu-11.x in the production environment, which is not connected through Internet. When I run apt-get install command, it gives me errors such as:
Depends: libc6-dev but it is not installable
Depends: gcc but it is not installable ..........and so on
 
I have checked these packages through "dpkg --get-selections" command and i believe that they are already installed (probably virtual packages) in the system. Please let me know the quick way to complete this installation. 
 
Cheers....

---

### Post by dino99 on 2011-08-10
sroll down this howto:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

