---
title: "Unresolved Dependencies list for a package"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by blackcoatman on 2008-11-07
Hello
I'm looking for a way to check **offline **ALL the _unresolved_ dependencies of a .deb package (for instance, Blender: i have libc6, but i don't have libopenal, so i only want to know that i need libopenal and its own unresolved dependencies, if any), so that I can manually download _only _the ones I need. I have read a solution somewhere which involves generating a script from synaptic, but this won't do it for me, since I can't even update my apt package list from the repositories (so I'm stuck with just my installed packages and work just with sources or seperate .deb packages).

I'm desperate for this, please, I really wish someone knows!

---

### Post by cdtech on 2008-11-07
```
apt-cache depends pkg-name
```

This may help......

---

### Post by blackcoatman on 2008-11-07
Does this work somehow with external .deb files or does the package have to be in the apt list already? I mean, how can I have an external .deb package in my apt cache if I can't install it in the first place :P

---

