---
title: "Alternate Select and Install 85% Error"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by goku93 on 2012-12-27
Hello, I've a Pentium IV, 256MB of Ram, so i will use Lubuntu Alternate 12.10.
I've used Unetbootin, because i want to boot from USB instead of CD (DVD-ROM isnt working).

Im connected to internet, i've started the installation when it is in ''Select and Install'' it stucks on 85% and then it appears an error. Always in the same % the error appears.

I have checked the MD5 from the iso and is ok. So i dont know what is the error :(

4 days trying to install it, but well :(

Any help? :( thanks you.

---

### Post by goku93 on 2012-12-28
UPDATE:
Ok, i have tried installing it on Oracle VM, and i get the same error on 85%. (Already have downloaded again the iso)

---

### Post by ibjsb4 on 2012-12-28
What does the error say?

Try downloading from a different mirror.

---

### Post by goku93 on 2012-12-28
OK i will try from another mirror but this is the error:

[http://i.imgur.com/92MOA.jpg](http://i.imgur.com/92MOA.jpg)

---

### Post by ibjsb4 on 2012-12-28
Try these commands and post any errors.

```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
```

---

