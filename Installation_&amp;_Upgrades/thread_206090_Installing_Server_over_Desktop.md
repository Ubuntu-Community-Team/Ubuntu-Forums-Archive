---
title: "Installing Server over Desktop"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by sunny007 on 2006-06-29
Hi,

I installed destop version 6.06 successfully and it works fine. I would like to upgrade it so that I can run appche, mysql  and perl/php. I did install appache and mysql last. However, when I was installling it, I noticed one thing in "Not installed" category of packages that it show linux-server package. My understanding is desk-linux kernel and server-kernel are same. Is it correct assumption? if not, can someone explain me what are differences? 

Truely, one will say whay to go this path. I could have just installed LAMP and then kubuntu.  But I am new to linux. I am sure that I will do lot like this and then learn. But desktop help me lot for unstanding it. And do want to explore it more.

So please put some light on this as newbie can understand.

Thanks!

---

### Post by olsonar on 2006-06-29
i think the kernels are the same, but i'm not sure. I run apache2,mysql,perl,php on my ubuntu install using the 686 kernel no problem. just choose the desktop kernel corresponding to your processor. packages: linux-686 for intel processors, linux-k7 for AMD. if you have a dual-core processor be sure to get one with SMP(intel: linux-686-smp, AMD linux-k7-smp).

---

### Post by sunny007 on 2006-07-05
Thanks...So far I haven't seen any issue. I am still trying to explore it. I will post here if I see any difference.

---

