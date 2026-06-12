---
title: "kernel sources install"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by Erik. on 2006-10-22
Hi,
i am trying to install nDiswrapper but i got an error and i read everywhere that i need to install my kernel source but how can i install them? and how do i know thay have installed?

could someone help me please

---

### Post by bulldog on 2006-10-22
If you mean the kernel headers?
```
sudo aptitude install linux-headers-'uname -r'
```

---

### Post by Erik. on 2006-10-22
Hi,
i have done that and it says it does not found anything to install

when i go into the directory of ndiswrapper and i do make install i get the error:
```

root@EJP:~/Desktop# cd ndiswrapper-1.8
root@EJP:~/Desktop/ndiswrapper-1.8# make install
make -C driver install
make[1]: Map '/root/Desktop/ndiswrapper-1.8/driver' 
Can't find kernel sources in /lib/modules/2.6.15-27-k7/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Fout 1
make[1]: Map '/root/Desktop/ndiswrapper-1.8/driver' 
make: *** [install] Fout 2
root@EJP:~/Desktop/ndiswrapper-1.8#

```

what to do now???
what do i need to update?

---

### Post by bulldog on 2006-10-22
Well did you take a look if your kernel is in /lib/modules?

---

### Post by Erik. on 2006-10-22
When i look into that directory i see some maps whit some files into it thats all
i can not find a map build or a link build

---

