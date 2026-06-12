---
title: "installation of java"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by mahboob218 on 2013-06-07
hi everyone 

i have problem with java installation ,i m beginner for ubuntu ,i installed it few months ago ,now i java is removed and i want to install it .i tried many times with terminal but all in vain .i can't understand the formation of directories ,so i want to know any other way through i can install java without the formation of directories . i want to know the way i can install java without the use of terminal .

so plz help me if anyone knows about it .

---

### Post by slickymaster on 2013-06-07
> **mahboob218 said:**
> hi everyone 

i have problem with java installation ,i m beginner for ubuntu ,i installed it few months ago ,now i java is removed and i want to install it ...

IMHO, the best way to install Java is through the terminal, and you shouldn't be afraid of it because it's really simple to achieve it. All you have to do is to open a terminal window in your computer and copy/paste the following:```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```And that's it.
> **mahboob218 said:**
> ... i want to know the way i can install java without the use of terminal ...
If you want to do it without the use of the terminal just open Ubuntu Software Center, type 'Java' in the search field and hit the Enter key. Select the item OpenJDK Java 7 Runtime in the list and click on the 'Install' button at the right. And that's it.

---

### Post by mahboob218 on 2013-06-08
thanks slickymaster ,, it works

---

### Post by slickymaster on 2013-06-08
You're welcome. Glad you got Java installed as you intended.

---

