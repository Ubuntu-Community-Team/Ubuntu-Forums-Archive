---
title: "ubuntu 10.10 compatibility with my laptop"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by yashiez on 2011-04-07
Hi, guys.

I have installed ubuntu 10.10 in my laptop.. but its a very basic model.
it gives some wierd display before the  ubuntu login screen..
Its core is intel pentium dual core. 
Its ram is only 1gb without any graphic card or graphic accelerator.
I want to know if ubuntu 10.10 installs itself by adapting to my configuration , or it just tries to install the full version??? 
Because i have installed windows 7 , But it was installed according to the configs of my laptop , leaving out all the advanced graphics options..

Please tell me if i can do something about it, or should i use some old version of ubuntu ??

Thank You

---

### Post by Dutch70 on 2011-04-07
> **yashiez said:**
> Hi, guys.

I have installed ubuntu 10.10 in my laptop.. but its a very basic model.
it gives some wierd display before the  ubuntu login screen..
Its core is intel pentium dual core. 
Its ram is only 1gb without any graphic card or graphic accelerator.
I want to know if ubuntu 10.10 installs itself by adapting to my configuration , or it just tries to install the full version??? 
Because i have installed windows 7 , But it was installed according to the configs of my laptop , leaving out all the advanced graphics options..

Please tell me if i can do something about it, or should i use some old version of ubuntu ??

Thank You

what do you mean by "very basic model"?

What kind of weird display, is this causing you other problems?

1GB of RAM is plenty. To find out what your graphics card is, run the following command. Menu to applications > accessories > terminal and copy/paste this command.
```
lspci | grep VGA
```

Ubuntu installs whatever version you downloaded.

Do something about what??? A weird display before the login screen?

Please read this...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by Mark Phelps on 2011-04-07
> **yashiez said:**
> Hi, guys.

I have installed ubuntu 10.10 in my laptop.. but its a very basic model.
Which make and model? Telling us it is very basic is meaningless.

> it gives some wierd display before the  ubuntu login screen..
Once again, need details, not vague wording.

> Its core is intel pentium dual core. 
Its ram is only 1gb without any graphic card or graphic accelerator.
The 1GB is plenty but you must have a graphics chipset of some kind or you would not be seeing any display at all.  Once again, details would help.
> I want to know if ubuntu 10.10 installs itself by adapting to my configuration , or it just tries to install the full version??? 
Ubuntu installs are basically the same -- it tries to find drivers for your hardware, installs those automatically, and installs a small set of applications. There's no option to install different "versions".
> Because i have installed windows 7 , But it was installed according to the configs of my laptop , leaving out all the advanced graphics options..
By "it", do you mean Win7 or Ubuntu?  

You get the "advanced" graphics options in both by installing proprietary video drivers and related control apps.  Once again, need the details of what hardware you have to provide advice.

---

