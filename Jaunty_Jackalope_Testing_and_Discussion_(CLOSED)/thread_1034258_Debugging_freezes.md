---
title: "Debugging freezes"
date: 2009-01-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by marmuta on 2009-01-08
My jaunty install has recently been suffering from freezes like once a day or so. It mostly happens when I have a million windows open and do the one last fatal mouse click. Usually the cursor starts to stutter and after maybe 5 seconds everything just stops. I can't even ssh in and magic sysreq works only occasionally.

Now, this last time I noticed that mem-usage shot up right before it happened.
My question is, is there a neat tool to monitor per-process memory-usage over time, preferably with graphs and over the network?
I'm thinking of *cough* windows performance monitor.

---

### Post by plun on 2009-01-08
Yup, I have exactly the same challenge.

Also that it is a 100% hardlock/freeze so Magic SysRq is broken.

I wonder how Kerneloops handles kernel panics ??? 

Use top or htop from the terminal, conky is also a good choice for checking processes.  Gnomes system monitor can also be used.


EDIT Kerneloops not installed...:confused:
```

sudo apt-get install kerneloops
```

Package info
[http://packages.ubuntu.com/jaunty/kerneloops](http://packages.ubuntu.com/jaunty/kerneloops)

.

---

### Post by ShirishAg75 on 2009-01-08
I have kerneloops installed but don't know/see it helping in anyway.

---

### Post by plun on 2009-01-08
> **ShirishAg75 said:**
> I have kerneloops installed but don't know/see it helping in anyway.

Well, I can see huge reasons for installing kerneloops.

If Magic SysRq is broken the kernel must be frozen......


Also after **The Plumbers Big Bang** I can see even more reasons, mdz also changed it

[http://mdzlog.wordpress.com/2008/09/20/plumbers-conference-retrospective/](http://mdzlog.wordpress.com/2008/09/20/plumbers-conference-retrospective/)

> In between talks, I did some work on integrating apport with kerneloops.  The result is that kernel oopses can be captured as Apport problem reports with full detail, and semi-automatically filed as bugs, in addition to being counted on kerneloops.org’s statistics.  I’ve put an initial version into Ubuntu and sent the patch to Arjan for merging upstream, and we’re exploring the addition of kerneloops to our default installation to provide testing feedback to kernel developers from our users. 


Running my Vanilla kernel for a while.... no freezes yet.

---

### Post by marmuta on 2009-01-08
My current working model is that some process goes on a rampage and rapidly eats all available memory. I've seen the panels mem-monitor rise half a gig to the top seconds before. The oops if it happened would be secondary, but still good to look into. 
I'm still searching for a per-process history tool, but I guess I'll have to do some ps/top hackery.

---

### Post by ShirishAg75 on 2009-01-08
I have never used the Magic SysRQ , would try it though sometime. 

The combos are big and need to be posted somewhere. 

Found this [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

One thing though, is there anyway to know whether Magic SysRQ is enabled or disabled in the kernel without doing a Magic SysRQ sequence?

---

### Post by plun on 2009-01-08
Yup... maybe, my Vanilla also frooze..

This package might be the trouble maker and also "timing" when this started.

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002538.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002538.html)


I downgraded to Intrepids version, usplash_0.5.25_i386.deb ...  Testing...:)

---

### Post by plun on 2009-01-08
> **ShirishAg75 said:**
> 
One thing though, is there anyway to know whether Magic SysRQ is enabled or disabled in the kernel without doing a Magic SysRQ sequence?

Yup, you can check the kernel config within /boot 

But this has always been enabled and must be so for avoiding the power button and "hard" restarts which often damages a disk.

---

### Post by chrisccoulson on 2009-01-08
> **plun said:**
> Yup, you can check the kernel config within /boot 

But this has always been enabled and must be so for avoiding the power button and "hard" restarts which often damages a disk.

You can also disable/enable it at runtime (and check if it is enabled) by writing 1 or 0 to /proc/sys/kernel/sysrq

---

### Post by chrisccoulson on 2009-01-08
Also, Alt+SysRq can sometimes be useful for dumping information to a console (if you can recreate the crash there), as the information won't always get written to disk. In particular, Alt+SysRq+P will dump a call trace to the console if the machine is sufficiently alive, giving you some idea of what the kernel is currently doing (if you press it repeatedly whilst it is frozen and the call trace always looks the same, then it gives you an idea where it froze).

You need to change the console log-level to get it to dump the information to a console though:
```
echo 8 | sudo tee /proc/sys/kernel/printk
```

---

### Post by plun on 2009-01-09
Thanks chris for your tips !

Kerneloops catched it...


How it looks after reboot:

[IMG]http://ubuntu-pics.de/bild/8101/start4_5a7SSZ.jpg[/IMG]



**Apport also starts** but its broken with URL trouble to Launchpad.

Launchpad can also not handle a .crash file... must be renamed to a *.txt 


A bug nevertheless...

[https://bugs.launchpad.net/bugs/315199](https://bugs.launchpad.net/bugs/315199)


I suspect Xorg and nVidia drivers....

---

### Post by plun on 2009-01-09
Strange......  Please ignore

Test message, I posted a message hours ago..:confused:

---

### Post by ShirishAg75 on 2009-01-09
> **chrisccoulson said:**
> You can also disable/enable it at runtime (and check if it is enabled) by writing 1 or 0 to /proc/sys/kernel/sysrq

I guess this is the command to know what is the state at this moment. 

```


$ cat /proc/sys/kernel/sysrq
1

```

This shows that magicsysrq is enabled (I guess)

---

### Post by plun on 2009-01-09
Thread healed...:confused::P


The choice I got is to wait or blow out my system....

(EXT4 thread)

:)

---

