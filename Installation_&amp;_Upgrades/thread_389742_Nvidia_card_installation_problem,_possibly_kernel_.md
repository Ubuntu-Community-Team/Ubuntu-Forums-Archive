---
title: "Nvidia card installation problem, possibly kernel related. I am a complete noob!"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by zhongwei on 2007-03-21
Hello

Could someone please assist me. I have spent some hours trying to get my graphics card to work. It is eating into university study time :) 

I admit I am at a loss.. a little overwhelmed possibly. But I really want to stick with Ubuntu. I think this idea of a free operating system has much merit, my ignorance is still a contribution, developers can see from we noobs, on how to make it more user friendly...

attached is my nvidia installer log. could someone in the know please tell me what I need to do? In idiot step by step fashion. 

I note in this log that it says:

ERROR: The kernel source path '/usr/src/Linux-headers-2.6.15-28-amd64-generic'
       does not exist.  Please make sure you have installed the kernel source

please help

thanks

---

### Post by Rui Pais on 2007-03-21
> **zhongwei said:**
> 
ERROR: The kernel source path '/usr/src/Linux-headers-2.6.15-28-amd64-generic'
       does not exist.  Please make sure you have installed the kernel source


hi, 
have you tried first:
```
 sudo aptitude install linux-headers-2.6.15-28-amd64-generic
```

---

