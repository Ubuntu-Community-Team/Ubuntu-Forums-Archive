---
title: "Windows Application to Ubuntu"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by _albino_ on 2008-12-02
How can I install a windows application on ubuntu????

---

### Post by Diabolis on 2008-12-02
Use Wine: [http://www.winehq.org/](http://www.winehq.org/)
Its in the repo:
```
sudo apt-get install wine
```

You can also use Cedega, but you have to pay for it.

---

### Post by LeslieL on 2008-12-02
You can use Crossover, too, but you have to pay for it. Wine works very nicely for many things.

Another approach I've had to adopt for a few things: VirtualBox, which installs Windows as a program that runs under Linux, so you can have a Windows window open and hop back and forth with the click of a mouse. But it's a little complicated to install.

 Better still, see if you can learn to love native Linux applications that replace your Windows favourites. What are you trying to run?

---

### Post by Diabolis on 2008-12-02
Yeah virtualization is an option, except for gaming. I have used VMware, which is not too hard to install, and Qemu. Qemu is in the repo, so you are one apt-get install away from it.

---

### Post by Mark Phelps on 2008-12-02
Before you install Wine, suggest you go to the CodeWeavers site and check the list they have of Windows applications and how well they work in Wine.   Unless your particular apps have a high rating, you're wasting your time installing Wine.

---

