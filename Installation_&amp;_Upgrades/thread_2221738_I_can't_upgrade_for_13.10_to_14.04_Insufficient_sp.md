---
title: "I can't upgrade for 13.10 to 14.04 Insufficient space in /boot partition"
date: 2014-05-03
forum: Installation &amp; Upgrades
---

### Post by crislosi on 2014-05-03
Hi, I've got a /boot partition. When I want upgrade the OS I have this error message:

```
No hay espacio suficiente en el disco

La actualización se canceló. La actualización necesita un total de 57,2 M de espacio libre en el disco «/boot». Libere al menos 1.151 k de espacio en el disco «/boot». Pruebe vaciando su papelera y borrando paquetes temporales de antiguas instalaciones usando la orden «sudo apt-get clean».
```

I've deleted all old kernels and apt-get clean with ubuntu-tweak, and I've cleaned the root trash. The message tells to me that the system need 57,2 M free space in /boot and I have to liberate at least 1.151 k in /boot partition.

How can i solve this problem?

Thanks

---

### Post by monkeybrain20122 on 2014-05-03
Do a clean install. Why do so many people go through great length to 'upgrade' only to get a broken system?  A clean install takes about 15 minutes and if you have a separate /home you only need to reinstall the software, that take may be another 15-20 minutes.

---

### Post by ajgreeny on 2014-05-03
And please don't make a separate /boot partition again in a desktop system; it is a waste of time, disk space, and more often than not results in exactly the problems you have seen here.  By all means make a separate /home partition if you don't already have one as it does make upgrading distro version so much easier, but boot? No, don't bother!  Leave that for servers.

---

