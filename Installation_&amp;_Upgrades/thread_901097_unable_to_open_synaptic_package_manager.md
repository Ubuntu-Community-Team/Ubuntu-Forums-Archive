---
title: "unable to open synaptic package manager"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by nuke_fluke on 2008-08-26
I am unable to open synaptic package manager....
It gives the following error message

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]



So when I type the above command in terminal,
i get this

**dpkg: requested operation requires superuser privilege**

What do I do now?
I am not able to remove or install any software...

---

### Post by simbiwa on 2008-08-26
> **nuke_fluke said:**
> I am unable to open synaptic package manager....
It gives the following error message

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]



So when I type the above command in terminal,
i get this

**dpkg: requested operation requires superuser privilege**

What do I do now?
I am not able to remove or install any software...

Try typing " sudo dpkg --configure -a "

---

### Post by nuke_fluke on 2008-08-26
thanks ...it worked

I am now able to open the synaptic..

But the following message came in terminal:

[B]Setting up gcc-3.3-doc (1:3.3.6-15ubuntu4) ...
sh: cannot open /usr/share/info/gcc-3.3.info.gz: No such file
install-info(/usr/share/info/gcc-3.3.info.gz): 
dpkg: error processing gcc-3.3-doc (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gcc-3.4-doc (3.4.6-6ubuntu3) ...
sh: cannot open /usr/share/info/gcc-3.4.info.gz: No such file
install-info(/usr/share/info/gcc-3.4.info.gz): 
dpkg: error processing gcc-3.4-doc (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gcc-3.3-doc
 gcc-3.4-doc[/B]

Can you tell me what that means?

Before that let me tell you that the GCC I installed did not install properly as I have tried to run the simplest of C programs and it says
stdio.h does not exist...

How can I reinstall the whole GCC from scratch...

Thanks..

---

### Post by simbiwa on 2008-08-26
[http://www.linuxfromscratch.org/blfs/view/stable/general/gcc.html](http://www.linuxfromscratch.org/blfs/view/stable/general/gcc.html)

---

### Post by Ninjahedge on 2008-08-28
Thank you SO MUCH for the " sudo" at the start of the session.

Forgive my ignorance, but what does that command do that enables you to login as a superuser on Konsole?

---

