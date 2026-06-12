---
title: "kernel headers"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by t3rm1n8r1x on 2005-04-01
does anyone know where i can get kernel headers for kernel 2.6.8.1-3-386? i already looked in here: [http://higgs.djpig.de/ubuntu/www/](http://higgs.djpig.de/ubuntu/www/)

---

### Post by az on 2005-04-01
Look in synaptic.  You have them on your cd.

The package is called linux-headers.

Kernel-headres are debian, linux-headers are Ubuntu.

---

### Post by RHCEConvert on 2005-04-01
Do something like the following

myBashPrompt:~$ sudo apt-cache search headers | grep -i kernel

Should yield a nice list.  O:)

---

### Post by t3rm1n8r1x on 2005-04-01
[QUOTE=RHCEConvert]Do something like the following

myBashPrompt:~$ sudo apt-cache search headers | grep -i kernel

Should yield a nice list.  O:)[/QUOTE]
 maybe i should've mentioned i can't acces the internet directly through ubuntu. i download everything through winxp

---

### Post by az on 2005-04-02
Take two.

Look in synaptic. You have them on your cd.

The package is called linux-headers.

Kernel-headres are debian, linux-headers are Ubuntu.

---

