---
title: "My Ubuntu Lucid takes 1.5GB RAM doing nothing"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by AdyMareshal on 2010-05-23
I've installed Ubuntu 10.04 on my laptop (Intel core i3 2.5Ghz, 3GB RAM) and it's taking 1.5GB RAM doing nothing. This is what system monitor reports.

Is this a bug or something?

---

### Post by tada on 2010-05-23
I'm a newbie but I believe that the memory used here is effectively phantom - basically its trying its best to predict what you're going to do next so it has cached _everything_.

When you start to use it, it'll get a better understanding of what you're going to do this time and free up loads to do what you want it to.

---

### Post by dtfinch on 2010-05-23
What's using that memory?

---

### Post by fantomefreek on 2010-05-23
> **AdyMareshal said:**
> I've installed Ubuntu 10.04 on my laptop (Intel core i3 2.5Ghz, 3GB RAM) and it's taking 1.5GB RAM doing nothing. This is what system monitor reports.

Is this a bug or something?

Hi AdyMareshal !!!!
that may be a bug !!! I have Ubuntu 10.04 and normally my computer consumes between 300 and 400 MB RAM of 8 GB RAM !!!! Try to update your kernel or look for any process that is zombie or running and kill it if you don't use it !!!

---

### Post by Old_Grey_Wolf on 2010-05-23
> **AdyMareshal said:**
> I've installed Ubuntu 10.04 on my laptop (Intel core i3 2.5Ghz, 3GB RAM) and it's taking 1.5GB RAM doing nothing. This is what system monitor reports.

Is this a bug or something?

I have been using my laptop with 10.04 for the past 7 hours. I have opened the terminal, OpenOffice.org, VirtualBox, and so forth. I only have Firefox open at the moment, and the System Monitor shows I am using 340 MiB. 

Use the System Monitor to see if a process is using a lot a memory. In System Monitor you can sort the list of processes by memory usage.

---

### Post by bumanie on 2010-05-23
Type 'top' (without quotes) into terminal and then post a screenshot of the output - there is likely a process running that should not be. Depending on the process, you may be able to kill it or find some other solution.

---

### Post by nmaster on 2010-05-23
type ```
free -m
``` into the terminal.  that won't be wrong.

---

### Post by AdyMareshal on 2010-05-23
> **bumanie said:**
> Type 'top' (without quotes) into terminal and then post a screenshot of the output - there is likely a process running that should not be. Depending on the process, you may be able to kill it or find some other solution.

TOP COMMAND -> [http://i49.tinypic.com/20tknf8.png](http://i49.tinypic.com/20tknf8.png)
 
FREE COMMAND -> [http://i49.tinypic.com/1553xom.png](http://i49.tinypic.com/1553xom.png)

System Monitor Processes -> [http://i50.tinypic.com/2d1p98n.png](http://i50.tinypic.com/2d1p98n.png)

System Monitor Resources -> [http://i46.tinypic.com/344fqd5.png](http://i46.tinypic.com/344fqd5.png)

I have, like all others, Kernel 2.6.32-21.generic

---

### Post by dtfinch on 2010-05-23
In system monitor, click view->all processes.

---

### Post by AdyMareshal on 2010-05-23
> **dtfinch said:**
> In system monitor, click view->all processes.

Damn, there are way too many. 2 Xorg processes are eating 200MB ram

Many processes are sleeping there...

---

### Post by nmaster on 2010-05-24
> **AdyMareshal said:**
> Damn, there are way too many. 2 Xorg processes are eating 200MB ram

Many processes are sleeping there...

care to post the output of top, or free as people suggested?  perhaps screenshots if you're more comfortable with that?  the more details you give the better, there might not be a problem with lucid, it might be with a program you are running.

---

### Post by AdyMareshal on 2010-05-24
I've already posted the output of top

[http://i49.tinypic.com/20tknf8.png](http://i49.tinypic.com/20tknf8.png)

Do you need the entire text copied from console?

---

### Post by RealZeratul on 2010-05-24
Hi everybody,
I just registered to join the discussion because I had the same problem after I installed many updates this morning; Ubuntu normally uses about 330 MB of my physical memory, but after restarting it used about 1400 of my 1536 MB RAM, with no unusual processes showing up in top or the system monitor (especially no process with more than 70 MB memory consumption). The memory was not used as cache, but really in use; starting some memory intense scripts instantly made the system use the swap.

After restarting one or two more times (unfortunately, I can't remember), everything went back to normal (with the processes in system monitor pretty much exactely looking like before). I will keep an eye on this and tell you if it happens again. Also, is there any way to show the memory consumption of processes not showing up in the system monitor (with "All Processes" enabled of course)?

Edit: My system specs are Ubuntu 10.04 x86-64 running in a VirtualBox with "Guest Additions" under Win7 Pro x64, i7, 1.5 GB RAM allocated, ATI HD4570, if anybody cares. ;)

---

### Post by nmaster on 2010-05-25
> **AdyMareshal said:**
> I've already posted the output of top

[http://i49.tinypic.com/20tknf8.png](http://i49.tinypic.com/20tknf8.png)

Do you need the entire text copied from console?

sorry for missing that, i was expecting to see text instead of a screenshot.  my mistake.

is the output of top sorted by memory?  when in top, press 'm' and it will sort the processes by their amount of memory usage. 

 from what is there, it seems like firefox is using the most memory, but it seems to be using a reasonable amount.  

adryan, are you also running lucid in virtual machine?  if so, i don't think i know enough about virtualization to help.

---

### Post by AdyMareshal on 2010-05-25
Anyway, Now is using around 400MB with nothing, which is quite resonable. After all this, I fell like ubuntu is not for me. Too user friendly, short time releases. 

I need a very stable system, and I might switch to debian testing version. In vmware is using 90MB ram, ONLY. Maybe it takes only 90MB in vmware, we'll see tomorrow night.

Even Ubuntu Pocket editions takes me 180MB. Debian stable release has an older kernel and I don't have my network drivers there. Only the 2.6.32 kernel has them(Jmicron network card). I take the risk of using a testing version.

Ubuntu keeps crashing many times, and I mean crashing by that grey screen, something like not responding. I'll see what debian can do.

---

### Post by nmaster on 2010-05-28
> **AdyMareshal said:**
> Anyway, Now is using around 400MB with nothing, which is quite resonable. After all this, I fell like ubuntu is not for me. Too user friendly, short time releases. 

I need a very stable system, and I might switch to debian testing version. In vmware is using 90MB ram, ONLY. Maybe it takes only 90MB in vmware, we'll see tomorrow night.

Even Ubuntu Pocket editions takes me 180MB. Debian stable release has an older kernel and I don't have my network drivers there. Only the 2.6.32 kernel has them(Jmicron network card). I take the risk of using a testing version.

Ubuntu keeps crashing many times, and I mean crashing by that grey screen, something like not responding. I'll see what debian can do.


if you want something stable don't use the testing version of debian.  just use lenny (v 5.0.4)

---

### Post by marcottebj on 2010-05-28
Was it an upgrade from an earlier version, or a fresh install?

---

### Post by howefield on 2010-05-28
> **AdyMareshal said:**
> I have, like all others, Kernel 2.6.32-21.generic

What do you mean by "like all others" ?

2.6.32.21 isn't the current 10.04 kernel.

---

### Post by RealZeratul on 2010-07-06
Hi again, sorry for warming up this old thread, but it seems indeed to be connected to the Ubuntu's update feature, perhabs in connection with VirtualBox. The memory consumption often is extremely high at the first restart after getting updates (maybe only after kernel updates, I have to be more observant next time); again, do you have any advice on how to check which process is responsible? System monitor won't help as pointed out above.

Cheers!

---

