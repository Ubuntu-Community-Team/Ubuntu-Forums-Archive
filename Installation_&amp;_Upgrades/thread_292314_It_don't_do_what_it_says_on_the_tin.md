---
title: "It don't do what it says on the tin"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by John Morgan on 2006-11-03
I am sitting here using Windows, which galls, as I can't configure Ubuntu to do what it says on the tin.  I feel a bit of Pratt actually as I have been extolling the virtues of Ubuntu and Linux to others for sometime &#8211;almost to the point of evangelism &#8211;something I hate.  Despite instructions on the Xubuntu website and from others I cannot get the different desktops to load on my Ubuntu computer or on my Kubuntu computer.  See Screen dump below.

I have hit the ](*,).  I guess guys I am having a bad evening of it and want a rant but I am holding myself back on that one.  All help appreciated.

---

### Post by boban on 2006-11-03
What does this command returns:

```

sudo aptitude search ubuntu-desktop

```

?

---

### Post by electricshoes on 2006-11-03
Did you uncomment Universe and Multiverse Repositories?

```
 sudo nano /etc/apt/sources.list 
```

Uncomment those lines for universe and multiverse

```
 sudo apt-get update
sudo apt-get install xubuntu-desktop 
```

see if that works.

---

