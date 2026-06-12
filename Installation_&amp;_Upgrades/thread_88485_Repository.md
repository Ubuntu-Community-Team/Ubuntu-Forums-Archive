---
title: "Repository"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by moondogie on 2005-11-10
From the command line how do I get a list of all the available packages for Ubuntu ?
Thanks , Moondogie:)

---

### Post by rjwood on 2005-11-10
[quote=moondogie]From the command line how do I get a list of all the available packages for Ubuntu ?
Thanks , Moondogie:)[/quote]

You can do 
```
sudo synaptic
```

or you can enter synaptic through system>administration>synaptic package manager.

---

### Post by earobinson on 2005-11-10
I think this is what you are looking for:

```
apt-cache showpkg
```

note you will probaly want to use a (| grep), or (| less) for more info man it!

(I found this by typing man apt-get, then i looked at the see also and found apt-cache, so i typed man apt-cache)

---

