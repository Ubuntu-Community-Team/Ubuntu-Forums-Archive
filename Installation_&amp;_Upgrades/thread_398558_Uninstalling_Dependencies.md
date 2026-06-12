---
title: "Uninstalling Dependencies"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by Aravind Kumar on 2007-04-01
When I tried to install a software say, X, I had to install some dependent packages. Now if I install the software X the dependencies were not removed. So I believe that in due course the unwanted dependencies may get added up. Is there any solution to this???

---

### Post by louieb on 2007-04-01
Depends on how you installed software X. 
If you installed it through Synaptic or aptitude using the official repositories, then decide to uninstall it Synaptic/aptitude should remove any unused dependencies.

But if you go to site Z and download program Y and install it. Then decide to uninstall, your pretty much on your own to get rid of any orphaned packages it may leave behind. (lol Just like Windows).

---

### Post by zvacet on 2007-04-01
How can dependencies be unwanted?Program you installed need them to work,so I don´t understand why you want to remove something you need?

---

### Post by Aravind Kumar on 2007-04-02
I installed the software X form universe repository, but when I uninstalled that software all the dependencies were not removed!!!

---

### Post by louieb on 2007-04-02
> **Aravind Kumar said:**
> I installed the software X form universe repository, 
Installed how? Synaptic? Aptitude? apt-get?  apt-get has a know problem  regarding removal of dependencies.

Are you sure you didn't install software M and it has some of the same dependencies. They weren't removed because software M needs them? 

If you can rule out the above then congratulations you have found anther BUG. :lolflag: Report it with all the particulars and maybe they will name it after you.

---

### Post by zvacet on 2007-04-03
```
sudo apt-get remove --purge program
```

---

### Post by Aravind Kumar on 2007-04-03
Thank u for the suggestions but the code mentioned above didn't do the trick...

---

### Post by zvacet on 2007-04-03
```
sudo apt-get autoremove
```

---

### Post by Aravind Kumar on 2007-04-04
Ya I too saw this autoremove option in one of the Documentations but when I use such a option in the terminal, it says that autoremove is an Invalid operation...

---

