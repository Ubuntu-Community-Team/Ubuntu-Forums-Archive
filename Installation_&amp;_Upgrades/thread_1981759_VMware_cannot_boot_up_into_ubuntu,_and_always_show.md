---
title: "VMware cannot boot up into ubuntu, and always showed GNU GRUB window"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by Lazysheep85 on 2012-05-17
Hi everyone,

I am a new to use ubuntu. I installed Win7 on my PC, and used VMware to load ubuntu. But I deleted the ubuntu from the VMware library and re-downloaded a new one. Then when I opened VMware, and loaded the new ubuntu image, it showed the following 

     [FONT=&quot][ Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename. ][/FONT]
  
I tried to google some solutions, and one suggested to manually boot up linux as follows. 

grub>ls
grub>setup root=(hd0,msdos1)
grub>linux /vmlinuz root=(hd0,msdos1)/dev/sda ro quiet splash
....
 
but i cannot find any "sda*" folder/file under /dev. So what should I do to boot up into ubuntu?

---

### Post by jadtech on 2012-05-17
im a bit confused here

you are trying to install ubuntu dual boot along side windows ?? 

or you are trying to install wubi or you are already running ubuntu trying to install some type of server..

if you are trying to install ubuntu along side windows on it own partition go ti this link..

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

if your computer is 64 bit use the drop down menu  to select the 64bit image then click start down load.. 

once you have that ISO image get a blank dvd right click on the ISO file you down loaded and choose to burn it to  the DVD .. 

once that is done you now have a bootable disk that can test ubuntu install ubuntu on its own parttion or install wubi through windows..

---

### Post by jadtech on 2012-05-17
> **Lazysheep85 said:**
> Hi everyone,

I am a new to use ubuntu. I installed Win7 on my PC, and used VMware to load ubuntu. But I deleted the ubuntu from the VMware library and re-downloaded a new one. Then when I opened VMware, and loaded the new ubuntu image, it showed the following 

     [FONT=&quot][ Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename. ][/FONT]
  
I tried to google some solutions, and one suggested to manually boot up linux as follows. 

grub>ls
grub>setup root=(hd0,msdos1)
grub>linux /vmlinuz root=(hd0,msdos1)/dev/sda ro quiet splash
....
 
but i cannot find any "sda*" folder/file under /dev. So what should I do to boot up into ubuntu?

SDA wont be a folder it will be  the label used for your Hard drive over all 

exsample sda refers to  first drive in the system 

on that drive  sda1 frist partition

sda 2 second and so on

---

### Post by Lazysheep85 on 2012-05-17
> **jadtech said:**
> im a bit confused here

you are trying to install ubuntu dual boot along side windows ?? 

or you are trying to install wubi or you are already running ubuntu trying to install some type of server..

if you are trying to install ubuntu along side windows on it own partition go ti this link..

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

if your computer is 64 bit use the drop down menu  to select the 64bit image then click start down load.. 

once you have that ISO image get a blank dvd right click on the ISO file you down loaded and choose to burn it to  the DVD .. 

once that is done you now have a bootable disk that can test ubuntu install ubuntu on its own parttion or install wubi through windows..
Thanks jadtech.

I only installed Win7 on my PC, but I used VMware to run ubuntu virtually. I think it's kind of different from the dual-OS, and I had no idea about wubi either. 

I have got the VMware virtual disk file of ubuntu (.vmdk), and I can run it to boot into ubuntu. But after I deleted this file and downloaded another one, I tried to load the new VMware virtual disk file, it didn't work, and gave the error mentioned in my thread. 

So can you help me with this problem? 

Thanks,
Jessica

---

### Post by Lazysheep85 on 2012-05-17
> **jadtech said:**
> SDA wont be a folder it will be  the label used for your Hard drive over all 

exsample sda refers to  first drive in the system 

on that drive  sda1 frist partition

sda 2 second and so on
But when I list all under the path /dev in Grub window, I didn't see the label called "sda". 
So i think my situation is different from those online. I have no idea how to solve my problem.

---

