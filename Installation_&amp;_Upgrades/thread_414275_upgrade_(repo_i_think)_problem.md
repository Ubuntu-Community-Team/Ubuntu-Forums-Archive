---
title: "upgrade (repo i think) problem"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Balinsky on 2007-04-19
im trying to do the distro network upgrade from 6.10 to 7.04 and when i try to use the upgrade manager i get the following error
```

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.:
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

```

i think my config files are messed up somehow

thanks 
jeBsky

---

### Post by Bundai on 2007-04-20
I think I have the exact same problem but I think its because of the server load, still I think its weird that its always the same files and so on. Guess we have to wait for answers or the servers to free up.

Edit: Got it working.

---

### Post by Balinsky on 2007-04-20
did u do anything or did it just start working?

---

### Post by Balinsky on 2007-04-23
anyone? i am baffled here. i may just need to download a cd

---

### Post by zvacet on 2007-04-23
```
sudo aptitude update
```

---

