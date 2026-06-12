---
title: "Ubuntu studio - where are the audio apps?"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by Ferris on 2007-12-27
Hi,
I just installed Ubuntu Studio on my system. During the installation, I chose audio apps and ladpsa effects to be installed.
Now, in the Applications -> Audio and Video (or similiar) I cannot find the apps that I installed the os for... Wired, Muse, Ardour, etc. where are they? I don't think I should have installed additional packages... 
Pls help... : (

---

### Post by Partyboi2 on 2007-12-27
checked that they are installed you can do that by
```
dpkg -l package name
```
(change package name to name of the package you are looking for)
[I] or
If you want to look through the list 
[/I]```
dpkg -l |more
```

---

