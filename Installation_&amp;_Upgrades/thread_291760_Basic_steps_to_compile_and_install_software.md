---
title: "Basic steps to compile and install software"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by anyedge on 2006-11-02
Can someone help me?  I am wondering what are the basic steps necessary to compile and install software on your edgy?  I would appreciate in help in this.  Thank you in advance.

---

### Post by taurus on 2006-11-02
Before you can compile anything from source, you need to have a working GCC and a few other things.  Therefore, you need to install the build-essential package first.

```
sudo aptitude update
sudo aptitude install build-essential
```
Then, just read this link, Section 4, on how to install it.  If you still can't understand the whole process, post it back here and maybe I can explain it for you...

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

