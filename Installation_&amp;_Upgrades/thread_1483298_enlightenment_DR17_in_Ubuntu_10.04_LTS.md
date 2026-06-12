---
title: "enlightenment DR17 in Ubuntu 10.04 LTS"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by poyato on 2010-05-14
Does anyone know how to  install enlightenment in Ubuntu 10:04? 
On the site below, is  related to some versions, but do not have the 10.04. I use the Jaunty  Jackalope, or is there another way? 

Thanks!

[http://packages.enlightenment.org/ubuntu/](http://packages.enlightenment.org/ubuntu/)


The oficial website:
[http://www.enlightenment.org/](http://www.enlightenment.org/)
](*,)

---

### Post by kappa962 on 2010-05-14
It appears that there is a repo there for lucid there. Even though they claim to have Jaunty, Intrepid, and Hardy, the directory structure is actually Lucid, Karmic, and Jaunty. Did you try adding "deb [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) lucid main extras" to your sources.list?

---

### Post by poyato on 2010-05-14
yes  there is a repository for Lucidty. I will try and post the results here.

---

### Post by anjo_ed on 2010-06-10
Hi!
So, Poyato, do you did make the test ?

---

### Post by dezine on 2010-07-29
Was searching around on how to get e17 on 10.04 and found this thread. Figured I'd mention that adding the repo worked. Thanks.

---

### Post by DanRock007 on 2010-09-19
i will try the repo out, would love to have enlightenment onmy desktop!

---

### Post by DanRock007 on 2010-09-19
I can tell you that this works!!

---

### Post by rascal+1/2 on 2011-01-04
+1

---

### Post by Buddlespit on 2011-02-05
Don't forget to download [http://packages.enlightenment.org/repo.key](http://packages.enlightenment.org/repo.key)

Run [PHP]$cd Downloads
sudo apt-key add repo.key[/PHP] afterwards (I had to navigate to my downloads folder first).

---

### Post by sunewbie on 2011-08-14
I installed it but version is E16
(Added to sources --> added key --> downloaded using 
sudo apt-get install e17)

How can I upgrade it to Version E17
Ubuntu 10.04
I also have Gnome and KDE
Is it advisable to have 3 desktop environment?

---

### Post by Frogs Hair on 2011-08-14
I'm using E17 in 11.04 , but according to the link the E17 packages for 10.04 have been deleted from the repository . E17 is a complete rewrite of E16 and in heavy development . I was able to install the core packages but I have no way to update them . I have been looking for a software source list but every thing I have found for Ubuntu is pre 10.04.[http://www.ubuntuupdates.org/packages/show/188804](http://www.ubuntuupdates.org/packages/show/188804)

---

### Post by sunewbie on 2011-08-27
EDIT

I could install E17. 'About Enlightenment' says version 16.99.

This is also the version found in Bodhi Linux, which uses Enlightenment as default desktop and will push latest updates into repos.

---

