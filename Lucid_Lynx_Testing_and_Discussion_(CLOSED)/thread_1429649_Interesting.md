---
title: "Interesting"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sirkeith on 2010-03-14
I was using Synaptic to remove some unnecessary software yesterday and was quite surprised by the packages that would be taken out along with the chosen removal. Even with stuff called optional. In one case adding a package removed several other packages. :confused:

keith

---

### Post by Enigmapond on 2010-03-14
If you remove a package that has dependencies, they will also be removed. In the same token if you install something that will conflict with certain things, synaptic will remove the conflicts to allow installation of the chosen programme.

---

### Post by 23meg on 2010-03-14
You may benefit from reading [the sticky thread about partial upgrades]("http://ubuntuforums.org/showthread.php?t=1343434").

---

### Post by ajgreeny on 2010-03-14
> **Enigmapond said:**
> If you remove a package that has dependencies, they will also be removed. In the same token if you install something that will conflict with certain things, synaptic will remove the conflicts to allow installation of the chosen programme.
It is not true that removing a package will also remove its dependencies.  That will only occur if you are also installing something that will conflict with something that was a dependency and is no longer needed.

If you want to remove dependencies that are unwanted, you will need to use the filter on the left hand side of the synaptic window "Status", or use aptitude in terminal or ```
sudo apt-get autoremove
```If a package is still needed as a dependency of another installed package, it will not be removed by "autoremove", so this should be quite safe to use.

However, I suggest you proceed with some caution in these cases, as it is possible for the system to remove something that is an "autoremove" candidate, but which you still use and find useful.  Review the lists carefully before accepting them, a bit like "Computer janitor" which can remove useful programs.

---

### Post by emarkay on 2010-03-14
> **23meg said:**
> You may benefit from reading [the sticky thread about partial upgrades]("http://ubuntuforums.org/showthread.php?t=1343434").

Ah, but, is a "Synaptic" the same as a Update/Upgrade?  Here we see the failure in the system!
Too many ways to do the same thing and not enough ways to know what you are doing.
Then there's the "recovery menu's" "Fix Broken Packages" update/upgrades...   

(Oh my!)

---

