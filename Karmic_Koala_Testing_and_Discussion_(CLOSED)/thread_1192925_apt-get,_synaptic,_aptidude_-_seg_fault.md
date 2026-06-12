---
title: "apt-get, synaptic, aptidude - seg fault?"
date: 2009-06-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-06-20
```
root@puccaso-lp:~# apt-get dist-upgrade -V
Segmentation faultsts... 0%
root@puccaso-lp:~# 


root@puccaso-lp:~# aptitude dist-upgrade -V
Segmentation faultsts... 0%
root@puccaso-lp:~# 
```

what do i do?!

---

### Post by paul_in_london on 2009-06-20
Try this:

```
 sudo rm -vf /var/cache/apt/*.bin 
```

and then try to update/upgrade again.

If it doesn't work first time, reboot and repeat.

HTH

See [http://rubbad.wordpress.com/2009/01/02/segmentation-fault50/](http://rubbad.wordpress.com/2009/01/02/segmentation-fault50/)

Apologies for previous broken link!

---

### Post by Zorael on 2009-06-20
Your link is borked. :3

[http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/](http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/)

---

### Post by puccaso on 2009-06-21
> **paul_in_london said:**
> Try this:

```
 sudo rm -vf /var/cache/apt/*.bin 
```and then try to update/upgrade again.

If it doesn't work first time, reboot and repeat.

HTH

See [http://rubbad.wordpress.com/2009/01/02/segmentation-fault50/](http://rubbad.wordpress.com/2009/01/02/segmentation-fault50/)

Apologies for previous broken link!

thank youu

---

