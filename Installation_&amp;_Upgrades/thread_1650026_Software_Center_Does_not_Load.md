---
title: "Software Center Does not Load"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by Konoha on 2010-12-21
consultant@Konoha:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>
    import pygtk
ImportError: No module named pygtk
consultant@Konoha:~$ 


My Software Center does not work, i tires running it throught the terminal and the above is the error message i got, Please Help

 When i try to un it through the GUI is says its starting then disapears after a few seconds!:popcorn:
I cannot usu synaptic wathsu ma call it becaus its complicated and when i want to installl a program like skype i get loads of option and i do not know which one to choose!

SOS

---

### Post by PhantmKllr on 2010-12-21
Try

```
sudo apt-get install pygtk
```

---

