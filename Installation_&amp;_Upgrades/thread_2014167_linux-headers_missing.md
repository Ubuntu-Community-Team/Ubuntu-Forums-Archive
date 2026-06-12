---
title: "linux-headers missing"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by technewb on 2012-07-01
I am installing a new wifi driver and am in need of my kernel header files. Does anyone know where I can find kernel 2.6.35.11-perf header files? Or is there another solution? Say install a similar kernel's headers and rename the file?

---

### Post by Merrattic on 2012-07-01
Have you installed build-essential?

```
sudo apt-get install build-essential
```

If you are compiling this should take care of just about everything.

If not and you need the headers:
```
uname -r
``` and note the output, then
```
sudo apt-get install linux-headers-"content of uname -r"
```(no inverted commas!)

---

### Post by matt_symes on 2012-07-01
Hi

Just to reiterate the above post, the easiest way to get the correct headers is.
[FONT=monospace]
[/FONT]```
sudo apt-get install linux-headers-$(uname -r)
```This will install the correct headers for you current kernel version.

Kind regards

---

### Post by Merrattic on 2012-07-01
I knew that once, then forgot it, so opted for the easy (long) way. Thanks Matt :)

---

### Post by matt_symes on 2012-07-01
Hi

> **Merrattic said:**
> I knew that once, then forgot it, so opted for the easy (long) way. Thanks Matt :)

You did all the heavy lifting Merrattic :D

Kind regards

---

### Post by technewb on 2012-07-02
sudo apt-get install linux-headers-$(uname -r)
results in.  Package linux-headers-2.6.35.11-perf could not be found :(
Any idea what site I can add to my repository to locate this particular kernel header?

---

### Post by technewb on 2012-07-02
I found a place to download this whole kernel. Does anyone know how to or how hard it would be to open the deb package without installing and locate the header files? In that case I could just push the file to the appropriate directories.

---

### Post by matt_symes on 2012-07-02
Hi

> **technewb said:**
> I found a place to download this whole kernel. Does anyone know how to or how hard it would be to open the deb package without installing and locate the header files? In that case I could just push the file to the appropriate directories.

Can you post the link to kernel package you have found.

Can you also post the output of

```
uname -a
```and 

```
cat /etc/lsb-release
```I am interested in your current kernel and i assume it's not in the repos. How did you install it ? Where did you get it from ? Did you compile it yourself ?

Kernel headers normally get installed into /usr/src/<linux-kernel-name>.

Kind regards

---

### Post by technewb on 2012-07-02
Unnamed -a. Outputs:

```
Linux localhost 2.6.35.11-perf #1 SMP PREEMPT Mon Nov 28 19:31:07 KST 2011 armv71 GNU/ Li
``````
cat /etc/lsb-release. 
distribution_Id= ubuntu
Distribution_release= 10.04
Distribution_ code name= Lucid
Distribution_description= "Ubuntu 10.04 LTS"
```I installed it via a "backtrack install" app that I downloaded on my android. 

All I did was extract an image file to my sdcard and CD it via my command terminal. It came with a vnc viewer as well. 

To be honest I am a technewb :) and am just learning to use it. I am having problems figuring out where things are because I can only view root files via the vnc even though my phone is rooted. 

It seems weird that I call up backtrack and a few other programs from my sdcard yet their root files are located on my internal storage disc and like I said I can only view thoughs through the vnc.

---

### Post by technewb on 2012-07-02
[http://permalink.gmane.org/gmane.linux.kernel.announce/723](http://permalink.gmane.org/gmane.linux.kernel.announce/723)

In /use/sec I have headers for various kernels. None are of 2.6.35.11-perf. And no nothing in the repository. I need the header file to compile a driver for my wifi chipset. 

I have tried updating my backtrack version hpping that would solve some probs but it tries to load to much into my internal disc storage ( I only have a gig there). 

I can't figure out how to load it on my sdcard where I have ample space (where I put the current version image and sh file). 

I can't find a site to add to my repository. I have yet to try to open the deb file from the link above.

---

### Post by matt_symes on 2012-07-02
Hi

> <snip>armv71<snip>> I installed it via a "backtrack install" app that I downloaded on my android.This was quite an important piece of information you left out the first post.

I will take a look for you but please remember to include as much information in your initial post as possible. You will get pertinent help much quicker.

EDIT: Exactly what hardware is this kernel running on ? On your Android phone ?

EDIT2: For future reference maybe

[http://www.kernel.org/pub/linux/kernel/v2.6/longterm/v2.6.35/](http://www.kernel.org/pub/linux/kernel/v2.6/longterm/v2.6.35/)

Kind regards

---

