---
title: "Cannot change visual effects"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by infestor on 2010-04-11
in appearance preferences>visual effects i am stuck with none setting. whenever i click on normal or extra ubuntu searches for drivers and asks me whether to keep the new or previous setting but when i say ok it gets frozen!
any ideas to solve this issue?

---

### Post by trig on 2010-04-11
What drivers are you using? I have Nvidia version 185 installed.

---

### Post by infestor on 2010-04-11
> **trig said:**
> What drivers are you using? I have Nvidia version 185 installed.

i use 195.36.15 on 64bit lucid

---

### Post by infestor on 2010-04-11
do you think the problem is caused by the nvidia drivers version?

---

### Post by sparkus on 2010-04-11
same problem.

---

### Post by CryptoPaul on 2010-04-11
A temporary workaround is to force quit after making the changes.

This is a known bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/554106](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/554106)

---

### Post by infestor on 2010-04-13
after the last update to 2.6.32-20-generic kernel now it does not freeze but effects still persist on being on 'default' setting :(
also same for my laptop (lenovo sl500, intel gma gpu)
i guess it has nothing to do with nvidia drivers

---

### Post by tad1073 on 2010-04-13
Open a terminal and issue the command ```
sudo nvidia-xconfig
```


then reboot

---

### Post by infestor on 2010-04-14
> **tad1073 said:**
> Open a terminal and issue the command ```
sudo nvidia-xconfig
```


then reboot

doesnt work with me, tried several times

---

### Post by krige on 2010-04-15
Try running:
```
sudo apt-get install compiz
```

---

