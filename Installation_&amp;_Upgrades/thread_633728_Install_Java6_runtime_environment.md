---
title: "Install Java6 runtime environment"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by olsoveasna on 2007-12-06
Hi! Some people may ask why I posted something that could be found in this forum. Actually, I tried my best to find the answer to my problem, but all answers did not work to me. I tried to install Java 6 runtime environment in my Ubutu 7.04. During installation, I faced with co-dependency problem. File .bin depended on .jre and vice versa. Any help on this?

Note: I used dial up connection at home which did not allow me to install from internet. I downloaded required files in internet café and used offline installation.

Thanks

---

### Post by taurus on 2007-12-06
Where did you download it from?  Try downloading it from Sun's site and get the .bin file.  Then, you can install it with

```
cd ~/Desktop
chmod 755 **filename**.bin
sudo .**/filename**.bin
sudo update-alternatives java
java -version
```

---

### Post by bryle on 2008-03-05
Hi! I'm also installing java runtime 6 in my ubuntu 7, I followed the same procedure as what is given but i'm stuck in this error during my command: sudo update-alternatives java I got this error: unknown argument 'java'. What does this mean?

Thanks,
Bryle

---

