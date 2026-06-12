---
title: "Installing VMWare gett message unable to install: File not supported"
date: 2022-11-25
forum: Installation &amp; Upgrades
---

### Post by ozstar on 2022-11-25
I downloaded VMware for Linux from it's website and then clicked on it
  to install 
```
VMware-Player-Full-17.0.0-20800274.x86_64-bundle
```
but got this instead..

 > Failed to install file: Not supported

 Ideas please ?

Ubuntu 20.04

---

### Post by MAFoElffen on 2022-11-25
The syntax is:
```

sh VMware-Player-Full-17.0.0-20800274.x86_64-bundle --[option]

```
If just console/text install, then
```

sh VMware-Player-Full-17.0.0-20800274.x86_64-bundle --console

```
If GUI, then 
```

sh VMware-Player-Full-17.0.0-20800274.x86_64-bundle

```

---

### Post by ActionParsnip on 2022-11-28
or
```

chmod +x ./VMware-Player-Full-17.0.0-20800274.x86_64-bundle
sudo ./VMware-Player-Full-17.0.0-20800274.x86_64-bundle

```

---

