---
title: "Kernal upgrade for Pentium Processors"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by curiousnoob on 2007-09-20
While randomly searching the internet the other day I stumbled across an article, and forgot to bookmark it, that explained how the default kernal that comes with Ubuntu was designed to work for as many processors as possible.  
It went on to say that if you have a Pentium II or later, I have a Pentium 4, you could get a more specialized kernal that would give performance and stability boost.  
I cannot remember the instructions on how to locate this or install it other than one of the commands or lines was "linux-image".  
As you can tell I'm brand new at linux so I don't know enough yet to know where or how to look for things.  Hopefully one of you fine folks know what I am speaking of and can point me in th right direction.

---

### Post by logos34 on 2007-09-20
I think you need to custom compile it.  I'm not sure it's worth the time and hassle, but if you must:

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by curiousnoob on 2007-09-20
> **logos34 said:**
> I think you need to custom compile it.  I'm not sure it's worth the time and hassle, but if you must:

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
Definitely too complicated for me.  
I wonder if I am mixing things up in my head here.  
It seems to me that the article I read said you could find the right Kernal through Synaptic.  Does that ring any bells for anyone?

---

### Post by lopt on 2007-09-20
Well, agree its somewhat complicated, it doesn't help that umbuto has its own ways of doing things and also modify the code..

But if you only want to optimise the kernal for the pentium instead of the general standard 386, then its easy, just install the 686-kernel-package instead of the 386 installed default

sudo apt-get install linux-image-686

      //lopt

---

### Post by logos34 on 2007-09-20
> **lopt said:**
> But if you only want to optimise the kernal for the pentium instead of the general standard 386, then its easy, just install the 686-kernel-package instead of the 386 installed default

sudo apt-get install linux-image-686

      //lopt

I thought the '-generic' replaced the '-686'...I can't even find it in synaptic anymore.

---

### Post by Gremlinzzz on 2007-09-20
Heres how i upgraded my kernel to 2.6.22-11-generic

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by lopt on 2007-09-20
Well, I'm new to umbunto so I don't know how it treats defaults/generics but my old notebook that i digged out of the closet this evning had a default dapper on it that I never had continued on after testinstalled last year (until now when my new laptop ate its harddrive...)

But, without going into to technical language:
uname -a reported a 386 kernel
just installed the 686 image as above and uname now reports a 686 after reboot

Havent run any performance tools yet (any pointers to good ones) but it feels more responsive :-) even if the loadavergae lokks thevsame. now I only have to find something less demanding than GNOME...  2-4 Mb free memory with GNOME and firefox running....

---

oh
Well have not enough memory to play with the GUIs so i used apt-get directly, no idee how synaptic presents the package, but it should use the same descreptives?? I bloody hell hopes they all use the same database

---

### Post by curiousnoob on 2007-09-20
Is there any downside to upgrading to the 686 kernel?

---

### Post by logos34 on 2007-09-20
I don't think you can use the 686 unless you're running dapper or edgy.  It's been 'obsoleted' in feisty by the generic kernel

---

