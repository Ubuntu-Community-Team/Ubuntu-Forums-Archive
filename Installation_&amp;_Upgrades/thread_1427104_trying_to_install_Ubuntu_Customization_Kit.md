---
title: "trying to install Ubuntu Customization Kit"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by cry8wolf9 on 2010-03-11
im trying to install ubuntu customization kit with no luck i keep getting errors.ive tried from the terminal and i end up with this.
```

sudo apt-get install uck
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  uck: Depends: gfxboot but it is not installable
       Depends: squashfs-tools (>= 2.0) but it is not installable
       Depends: dpkg-dev but it is not installable
       Depends: build-essential but it is not installable
       Depends: bzr but it is not installable


```then i tried downloading it using this[ link ]("http://uck.sourceforge.net/download")
and i end up with this error 
```

Error: Dependency is not satisfiable: gfxboot

```

---

### Post by wojox on 2010-03-11
What happens if you try to download it from Synaptic Package Manager?

---

### Post by Kevbert on 2010-03-11
Synaptic and 9.04 work fine. There are 8 files downloaded and installed via Synaptic.

---

