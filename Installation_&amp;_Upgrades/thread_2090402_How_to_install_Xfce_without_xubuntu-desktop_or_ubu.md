---
title: "How to install Xfce without xubuntu-desktop or ubuntustudio-desktop"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by Random20210831 on 2012-12-02
I want to install Xfce **without xubuntu-desktop or ubuntustudio-desktop** (**original Xfce 4.10, without extras**). I too want to keep Unity (and Unity 2D) on my computer. Are the **xfce-meta** package great for that?
Thanks in advance!

---

### Post by ajgreeny on 2012-12-02
If this is on 12.04 you will need to enable the xfce4.10 ppa first then simply install xfce (maybe xfce4, I can't remember, and I'm on 10.04 at the moment).

As you suspect, that is a metapackage that tells the system what packages to install to give you xfce 4.10 without all the xubuntu apps that you may not wish to add.

[http://ubuntuforums.org/showthread.php?t=1972548](http://ubuntuforums.org/showthread.php?t=1972548)

---

### Post by Cheesemill on 2012-12-02
You could also try:
```
sudo apt-get install --no-install-recommends xubuntu-desktop
```
This will install only the packages that are necessary for XFCE without pulling in all of the default Xubuntu applications.

---

### Post by ibjsb4 on 2012-12-02
Why not just XFCE?  Or does that package no longer exist in 12.10?

sudo apt-get install xfce

---

### Post by Bucky Ball on 2012-12-02
It is:
```

sudo apt-get install xfce4
```That's it. Nothing else. That easy. Log out, choose from the Sessions pop-up. Log in. You're there ...

You can also search for xfce4 in Synaptic Package Manager or Software Centre and install from there.

---

### Post by ibjsb4 on 2012-12-02
woops

---

### Post by Random20210831 on 2012-12-02
> **Bucky Ball said:**
> It is:
```

sudo apt-get install xfce4
```That's it. Nothing else. That easy. Log out, choose from the Sessions pop-up. Log in. You're there ...

You can also search for xfce4 in Synaptic Package Manager or Software Centre and install from there.
Thanks! That works!

---

### Post by Bucky Ball on 2012-12-02
Enjoy! I love Xfce and Xubuntu is my main squeeze. ;)

---

### Post by Frogs Hair on 2012-12-02
Install the xfce-goodies package also.

---

### Post by ibjsb4 on 2012-12-02
> **Frogs Hair said:**
> Install the xfce-goodies package also.

Looks like a real good idea  :)

[http://packages.ubuntu.com/quantal/xfce4-goodies](http://packages.ubuntu.com/quantal/xfce4-goodies)

```
sudo apt-get install xfce4-goodies
```

---

### Post by Random20210831 on 2012-12-02
I seen these in grub... no! I want ubuntu, no debian grub!
[ATTACH]228106[/ATTACH]
How to reset grub splash to ubuntu default?

---

### Post by Bucky Ball on 2012-12-02
That means little. Install Grub Customizer and easily change the splash to whatever you want:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by Random20210831 on 2012-12-03
> **Bucky Ball said:**
> That means little. Install Grub Customizer and easily change the splash to whatever you want:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)OK. Thanks!

---

