---
title: "Python"
date: 2022-06-15
forum: Installation &amp; Upgrades
---

### Post by zongmans on 2022-06-15
what does this error mean

dependency is not satisfiable: python-gt4 (>= 4.10)

---

### Post by ajgreeny on 2022-06-15
There is no package python-gt4 in Ubuntu repos.

What are you doing and what needs it as a dependency, ie, what are you trying to install that requires it to also be installed?

PS:
The  (>= 4.10)  means the system is looking for that package of version equal to or higher than 4.10 but as it's not in the repos that is no help to you.

---

### Post by zongmans on 2022-06-15
i want to install resetter but apparently on 20.04 is not possible, right?

If so, tell me how to reset the computer to factory settings

---

### Post by zongmans on 2022-06-15
Before memory selection

---

### Post by deadflowr on 2022-06-15
I'm sure it suppose to be python-qt4 which does not exist in 20.04.
Can be found in Ubuntu 18.04's archives though.
The reason is because qt4 has been retired and most packages have been removed from the archives of newer versions of Ubuntu.

Looking at this tutorial: [https://vitux.com/how-to-reset-ubuntu/]("https://vitux.com/how-to-reset-ubuntu/")
It seems that author had the package already installed, perhaps it's an upgraded release.

---

### Post by Holger_Gehrke on 2022-06-15
And looking at the github repository that tutorial links to, one finds out that this is a dead project which hasn't been maintained for more than two years. It did make the jump to python3 and qt5. The 'issues' section of the repositories has several posts by people who tried to use it on more modern systems and 'succeeded' in **breaking** their systems. Unless you know your way around python and can fix this program yourself you should keep well away from it.

Holger

---

