---
title: "Synaptic Package Manager Error"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by F0B on 2010-05-05
Dear ubuntu friends,
I am new to Linux OS. 
I have installed ubuntu 9.10 successfully, and now try to installed some applicatiion from DVD repo using Synaptic Package Manager but I am getting error with My synaptic package Manager. I probably made mistake when using DVD repo.
 
error notification as below :
E:Malformed line 1 in source list /etc/apt/sources.list (URI)
E:The list of sources could not be read
Go to the repository dialog to correct the problem.
E:_cache->open()failed, please report
 
Pls help me how to solve.
Sorry for my poor english
 
F0B

---

### Post by mikewhatever on 2010-05-05
You'll have to edit the file it complains about. Post the content here first to check what's wrong with it.

```
gedit /etc/apt/sources.list
```

---

