---
title: "Problem with libgconf2-4"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by diamanthunden on 2008-09-16
Hey

I just upgraded to Hardy but after reboot it complained it couldn't find Human.xml. But I think now i've manually installed the artwork and that problem is maybe solved. But after login there's no desktop. 

In the terminal i cannot run anything dpkg, it just states that tons of dependencies are missing (see [http://ubuntuforums.org/showthread.php?p=5793520#post5793520](http://ubuntuforums.org/showthread.php?p=5793520#post5793520)). So supposedly the problem is that libgconf2-4 is not properly installed. I managed to download the package, but how do I install it by hand? If that is the solution?

I hope it makes sense - thanks ;)

---

### Post by zvacet on 2008-09-16
Go to the directory in which you downloaded package and run in terminal

```
sudo dpkg -i packagename
```

---

