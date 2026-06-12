---
title: "I cannot remove 2.6.28-10"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-03-19
During my use of Jaunty, I've seen the kernel move from 2.6.28-9, then to 2.6.28-10, and finally to 2.6.28-11. After updating the kernel, I remove the old one after I reboot. This time I was a bit late and was two versions ahead before I had a chance to remove the old kernels. I removed 2.6.28-9 from Adept but kernel 2.6.28-10 is not listed in Adept so I cannot remove it. I tried removing it from the command line but it can't find it, but I know it's installed. :(

---

### Post by rburkartjo on 2009-03-19
jla this should help

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by taavikko on 2009-03-20
Ok, use "aptitude search linux-image-2.6.28" or "dpkg -l |grep linux-image-2.6.28" to list 
it line starts with "i" or "ii" it means it's installed.

Remove with "sudo aptitude purge X"
X being the something like, "linux-image-2.6.28-9-generic"

---

### Post by dentaku65 on 2009-03-20
You can remove it with apt-get
```
sudo apt-get --purge remove linux-image-2.6.28-10[COLOR="Red"]-generic[/COLOR]

```
The part in [COLOR="Red"]red[/COLOR] may vary depending of the type of your machine

---

