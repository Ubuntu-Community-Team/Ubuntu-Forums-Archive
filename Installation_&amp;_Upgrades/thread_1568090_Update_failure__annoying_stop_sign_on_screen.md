---
title: "Update failure / annoying stop sign on screen"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by marsters256 on 2010-09-04
Ubuntu computer janitor in Ubuntu 10.04

```
Could not install updates

installArchives() failed
```at the top right of my screen, when i hover mouse over the 'red stop sign' It also says : 

```
An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was: 'Error: Opening the cache (E:Could not opent file /var/cache/apt/srcpkgcache.bin - open (13: Permission denied), E:The package lists or status file could not be parsed or opened.) 'This usually means that your installed packages have unmet dependencies
```Is it planning on **telling me** what packages have unmet dependencies? I don't think it is and there's no way to find out. 

I think I ran ```

chmod -R 775 /var/* 
```at some point if that helps because I was trying to sort out **another** issue that something was giving me that also said something about permissions. 

Ubuntu is just doing my head in tonight. :)

---

