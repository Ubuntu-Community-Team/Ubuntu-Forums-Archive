---
title: "installing ubuntu 10.10 on a new laptop HP G62 - B45"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by ipmurali on 2011-02-28
Hi guys,

I am facing problem while installing ubuntu 10.10 on a newly purchased laptop HP G62 - B45,  

Problem: Screen becomes blank after selecting language and press Forward.
 
I can run the live CD.
I can install from wubi(like a windows application)
But I could not install to a new partition.

As mentioned in link 
[http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10)
thread, i tried by pressing F4 while booting from CD.
but i am not getting the "Safe graphics mode" mentioned here.

below is the configuration of the laptop

3 GB RAM,
320 GB HDD,
512 MB Dedicated Graphics
ATI graphics 

-- thanks in advance --

---

### Post by sikander3786 on 2011-02-28
Please see here if it is of any help to you.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by ipmurali on 2011-03-02
Yes, that did the job.

I did it by giving the parameter
radeon.modeset=0 for Radeon (ATI graphics).

Thanks a lot Sikander.

---

### Post by Skaivalyas on 2011-11-08
Hey, How did you do that...??? I am facing a same problem with my HP pavilion g4 having ATI graphic card in it. I first installed an Ubuntu 11.04 in windows and rebooted it. When it gets highlighted on Ubuntu in the grub, I went on the "safe mode" in it. When I pressed 'e', a lot of text appeared in which I removed the "quite splash" and then replaced it with "radeon.modeset=0" and then pressed ctrl+x. It process with something and it is again showing me a blank screen. At first, there is no option of "radeon.modeset=0" when we press F6 in the picture shown. I did that also....
        I really don't know about installing an OS. So kindly help me.... Can you tell me the steps that you followed...???

---

