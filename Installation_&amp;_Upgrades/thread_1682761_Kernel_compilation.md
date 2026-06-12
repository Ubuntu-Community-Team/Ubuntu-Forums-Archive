---
title: "Kernel compilation"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by yannifan on 2011-02-06
Hello

I have Ubuntu 10.10 installed running kernel 2.6.35

I have to compile a kernel with some changes and tried the same with 2.6.36.

Instructions followed :
[http://www.cyberciti.biz/tips/compil...kernel-26.html](http://www.cyberciti.biz/tips/compil...kernel-26.html)

/boot listing after the process
abi-2.6.35-22-generic memtest86+_multiboot.bin
abi-2.6.35-24-generic System.map-2.6.35-22-generic
config-2.6.35-22-generic System.map-2.6.35-24-generic
config-2.6.35-24-generic System.map-2.6.36
config-2.6.36 vmcoreinfo-2.6.35-22-generic
grub vmcoreinfo-2.6.35-24-generic
initrd.img-2.6.35-22-generic vmlinuz-2.6.35-22-generic
initrd.img-2.6.35-24-generic vmlinuz-2.6.35-24-generic
initrd.img-2.6.36 vmlinuz-2.6.36
memtest86+.bin
sudhix@sudhix:/boot$


Error received during boot :
[http://img18.imageshack.us/i/06022011111.jpg/](http://img18.imageshack.us/i/06022011111.jpg/)

Am I missing any step here.

Please help
Thanks.

---

### Post by dino99 on 2011-02-06
i've never compiled, too lazy

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by yannifan on 2011-02-06
Unfortunately i have no choice. Have to since im supposed to make some source code changes.

---

### Post by yannifan on 2011-02-07
Fixed this issues 
Ran this command 
update-inintramfs -c -k 2.6.20

Source : [http://www.linuxquestions.org/questions/debian-26/modprobe-fatal-could-not-load-lib-modules-modules-dep-335214/](http://www.linuxquestions.org/questions/debian-26/modprobe-fatal-could-not-load-lib-modules-modules-dep-335214/)

---

