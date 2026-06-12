---
title: "Can't install anything through the Software Center"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by x1ph1as on 2012-02-29
As the title says, I can't install anything through the Ubuntu Software Center. I just get this message:

"Failed to download package files
Check your Internet connection"

And yes I have Internet connection! I don't know whats wrong and I would really appreciate some help figuring this out. I'm pretty new to Ubuntu so I don't really know where to start.

Has been like this since I updated to Ubuntu 11.10.

Help me pls.

---

### Post by yo_bhan on 2012-02-29
try from terminal is there any problem there?

---

### Post by x1ph1as on 2012-02-29
How do I install something I find in the Software Center through the terminal? As I said befor, Im new.

---

### Post by yo_bhan on 2012-02-29
> **x1ph1as said:**
> How do I install something I find in the Software Center through the terminal? As I said befor, Im new.

```
sudo apt-get install package_name
```for remove
```
sudo apt-get remove package_name
```for each line, usually you asked your root password. just type in there and press enter.
thats it.
usefull guide book, You can read it :D
```
http://www.makeuseof.com/pages/ubuntu-an-absolute-beginners-guide
```hope it help ;)

---

### Post by lowbudgetlaptops on 2012-02-29
how are you connecting ? please powerdown everthing computer  router modem etc... power back on check your connection and check it twice

---

### Post by x1ph1as on 2012-02-29
Seems to be working with the terminal... stupid Software Center :P

Thank you for your help!

---

