---
title: "usb permissions problem/installing from usb storage"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by pepollopep on 2008-05-11
I am 
working on a old dell with no cd drive.  I have managed to get damn small linux running on the machine through the usb, but want to 
install ubuntu.
I was trying to follow the instructions at 
<a href="https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html">preparing files for memory stick booting</a>

but cannot get past the initial step:

sudo zcat boot.img.gz > /dev/sda1

due to the error 

bash: /dev/sda1: Permission denied

My flash drive is definitely mounted on sda1, and if I navigate to it I can read, write and execute files.  


thanks for any help!

---

### Post by exaviorn on 2008-05-11
What user owns the external hard disk,that might be the problem:)

---

