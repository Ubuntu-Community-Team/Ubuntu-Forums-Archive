---
title: "Reinstall all packages after disk crash repair"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by odror on 2011-11-13
OS: ubuntu 11.10

Hi My ssd drive of the root partition had a a segment with i/o error. I was able to copy almost most of my staff to an alternate disk, but some of the applications have incorrect permission. I would like to reinstall all the packages so that the permission of the installed packages will be correct. Is there a way of doing that?. Reinstalling ubuntu is not the answer that I am looking for.

Thanks

---

### Post by BillyBoa on 2011-11-13
You could download Synaptic and do the reinstall from there, but if your machine is not working this solution is impossible.
You could do a CD based upgrade. You have to search the forum how you can upgrade your system not by internet, but through a CD.

---

### Post by odror on 2011-11-13
> **BillyBoa said:**
> You could download Synaptic and do the reinstall from there, but if your machine is not working this solution is impossible.
You could do a CD based upgrade. You have to search the forum how you can upgrade your system not by internet, but through a CD.

The system boots and works somewhat, but many of the symbolic links are incorrect as well as permission. Synaptic works, I need to reinstall 3000 packages. How can you make synaptic reinstall everything

---

### Post by BillyBoa on 2011-11-13
If synaptic is working try to find the broken packages.

---

### Post by odror on 2011-11-13
> **BillyBoa said:**
> If synaptic is working try to find the broken packages.
I do not know which one is broken. I found a few. this is why I would like to reinstall everything.

---

### Post by BillyBoa on 2011-11-13
From synaptic there is a filter to find broken packages. Find them and restore them. Also you could manually reinstall some of them, if you know which are failed. 

In any case mark from the Thread options the thread as UNSOLVED to attract attention from other users.

---

### Post by odror on 2011-11-13
> **BillyBoa said:**
> From synaptic there is a filter to find broken packages. Find them and restore them. Also you could manually reinstall some of them, if you know which are failed. 

In any case mark from the Thread options the thread as UNSOLVED to attract attention from other users.

Thanks I will try it tomorrow. It is late now here.

---

### Post by BillyBoa on 2011-11-13
Another solution

Restart your computer and from the Grub panel choose the second option (recovery mode)

Search for the terminal and execute:

```
fsck
```

if you like to avoid clicking yes for all the packages repaired

```
fsck -y 
```

fsck will check your file system and search for the problems should be fixed or corrected.

---

