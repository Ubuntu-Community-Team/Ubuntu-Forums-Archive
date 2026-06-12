---
title: "grub4dos  activating   Lubuntu"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by glene77is on 2012-06-19
Have a grub4dos booting system of several OS. 
Have installed Lubuntu. 
grub4dos activates Lubuntu by finding /boot/grub/core.img , 
then loading that core.img. 

core.img presents a basic grub2 type menu, 
which I would like to edit 
so that the menu is more presentable 
(with splash for example). 

Question: 
what program  does core.img  call in order to startup Lubuntu.
Question:
Are there any scripts that can be modified. 

Have experience modifying grub2 menus 
(via the .10,.20,.30,.40 code 
which produces the grub.cfg module.) 

Thanks. glene77is :)

---

### Post by darkod on 2012-06-19
Not sure about splash specifically, but another file that hold many grub2 options is /etc/default/grub.

---

### Post by glene77is on 2012-06-20
> **darkod said:**
> Not sure about splash specifically, but another file that hold many grub2 options is /etc/default/grub.

Darkod,
Thanks.
grub4dos provides an 'OK' splash.  I'll run with that. 
This is my code for kickstarting Lubuntu, from grub4dos.

```

# title  ==={1} LUbuntu }=== \n  ==={ LUbuntu find, load core.img }=== 
# ## set #2 HD
# lock
# root (hd0,1)
# find --set-root --ignore-floppies --ignore-cd /boot/grub/core.img
# ## kickstart the bootloader
# kernel /boot/grub/core.img

title  ==={ LUbuntu }=== \n  ==={ LUbuntu find, load core.img }=== 
	lock
	root (hd0,1)
	find  --set-root  --ignore-floppies  --ignore-cd  /boot/grub/core.img
	kernel  /vmlinuz  root=/dev/sda5  ro  quiet
	initrd  /initrd.img

```

Will check   /etc/default/grub  as you suggested. 
Since I need to move on,  
Consider this thread SOLVED.

glene77is     ):P

---

