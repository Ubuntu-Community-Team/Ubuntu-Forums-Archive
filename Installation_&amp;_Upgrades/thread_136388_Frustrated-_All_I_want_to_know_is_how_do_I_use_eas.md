---
title: "Frustrated- All I want to know is how do I use easy ubuntu."
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by YellowHat on 2006-02-25
It says it can't be accessed unless used by root account. So I'm going to have to go into command line mode. One problem....I don't know how to use the command line.

so what do I do? sudo su

admin@ubuntu: Home/Desktop/wherever the hell my stuff is and press ok

or is it admin@ubuntu install Home/Desktop/where the hell my stuff is.

I just want to install easy ubuntu. But it says I must be logged into my root account...yeah.

---

### Post by YellowHat on 2006-02-25
And, it keeps saying I should run this program as root user. I don't know what the hell I'm supposed to do.

---

### Post by John.Michael.Kane on 2006-02-25
[http://ubuntuforums.org/showthread.php?t=126070&page=4](http://ubuntuforums.org/showthread.php?t=126070&page=4)

```
sudo apt-get install subversion
svn co svn://freecontrib.org/easyubuntu/
cd easyubuntu/trunk/
sudo ./easyubuntu.py
```

---

