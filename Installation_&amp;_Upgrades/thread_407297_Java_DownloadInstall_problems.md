---
title: "Java Download/Install problems"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by Hitman0187 on 2007-04-12
I am new to Ubuntu, i was introduced to it by a friend and i am trying to download java but i have been having this same problem. It deals with something about the associated helper does not exist please change assoication in prefrences or something. I cant seem to figure it out and i was wondering if anyone could help me. 

THANKS :)

---

### Post by josephus on 2007-04-12
You need to be a little bit more detailed in explaining your problem. How are you trying to install Java?  And which helper program is it looking for?

I find that the easiest way to java is by using synaptic (system->administration->synaptic). You need to make sure that repository includes the multiverse and the backports, and you can do that by going in to the Settings->Repositories and checking off the appropriate boxes.

Then search for sun-java6 and install the packages that you want (you probably want sun-java6-bin, sun-java6-jre, and sun-java6-plugins).  After you've installed them go a terminal and 

```
sudo update-java-alternatives -s java-6-sun
```

This will update the system so that it will know to use the newly installed version of java.

---

### Post by aysiu on 2007-04-12
Try this:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Hitman0187 on 2007-04-12
It says when i go to the java website and try out all the different java's for ubuntu it says the assoicated helper files do not exist. I am trying different ways to download it or whatever to make it work. I cant seem to find the multiuniverse thing as well because you need that to be on to have java work

---

### Post by aysiu on 2007-04-12
I don't know what associated helper files are, but you can enable the Multiverse thing by following [these instructions](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories).

---

### Post by zvacet on 2007-04-12
system>administration>software properties Chek all boxes and reload.Chek your source list.
```
gksudo gedit /etc/apt/sources.list
```
 
This is example how it is supose to look
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse
**and not**
#deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse
If all your lines are O.K.
```
sudo aptitude update
```

After that you will find Java in synaptic.Search** sun**

---

### Post by phossal on 2007-04-13
You can just download Java from SUN. It's packaged in a .bin file. The version you get with Synaptic is just packaged *again*. It's slow to update, and it's unnecessarily complex to deal with. If you're looking for an easy, straightforward way to stay current, you can use the 3-step tutorial in my sig.

---

