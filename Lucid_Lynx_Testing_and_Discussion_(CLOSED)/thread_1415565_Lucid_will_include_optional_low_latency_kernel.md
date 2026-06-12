---
title: "Lucid will include optional low latency kernel"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by NightwishFan on 2010-02-25
[http://packages.ubuntu.com/lucid/linux-preempt](http://packages.ubuntu.com/lucid/linux-preempt)
[http://www.phoronix.com/scan.php?page=news_item&px=Nzg5Mw](http://www.phoronix.com/scan.php?page=news_item&px=Nzg5Mw)

This kernel will be useful for those that want lower latency for a game server or desktop. Currently there is only a 64-bit build. I do not know if a 32-bit one is planned. I am using it on my desktop and it works quite well. 

Here are the differences between the lucid generic and the preempt kernel.

```
# Linux kernel version: 2.6.32-14-generic		      |	# Linux kernel version: 2.6.32-14-preempt
# Sat Feb 20 05:18:09 2010				      |	# Sat Feb 20 07:45:15 2010
CONFIG_VERSION_SIGNATURE="Ubuntu 2.6.32-14.20-generic"	      |	CONFIG_VERSION_SIGNATURE="Ubuntu 2.6.32-14.20-preempt"
CONFIG_PREEMPT_VOLUNTARY=y				      |	# CONFIG_PREEMPT_VOLUNTARY is not set
# CONFIG_PREEMPT is not set				      |	CONFIG_PREEMPT=y
CONFIG_HZ_100=y						      |	# CONFIG_HZ_100 is not set
# CONFIG_HZ_1000 is not set				      |	CONFIG_HZ_1000=y
CONFIG_HZ=100						      |	CONFIG_HZ=1000
							      >	CONFIG_DEBUG_PREEMPT=y
							      >	# CONFIG_PREEMPT_TRACER is not set
```

---

### Post by svaens on 2010-03-26
Hi , and thanks for the information.

I was wondering. These days, is there any reason not to use the low -latency kernel by default? 

that is; What advantages do we (still) have in using the default non-low-latency kernel ?

thanks!

---

### Post by ghindo on 2010-03-26
What does a low-latency kernel entail?  I read both articles linked here, but I don't really understand what a low-latency kernel *does* it is.

---

### Post by jpeddicord on 2010-03-26
I may be wrong, but I believe low-latency is good for audio and the like, where any delay can cause sound lag. A low-latency (realtime?) kernel would respond more quickly to certain events, but it would likely consume more power as well.

---

### Post by Zerp64 on 2010-03-27
> **jpeddicord said:**
> I may be wrong, but I believe low-latency is good for audio and the like, where any delay can cause sound lag. A low-latency (realtime?) kernel would respond more quickly to certain events, but it would likely consume more power as well.

Are you sure that the low-latency kernel is the same as the realtime kernel? The realtime kernel is only useful for audio production, I thought.

---

### Post by aviramof on 2010-03-27
he had asked it in brackets and with a question mark so i'm quite sure he's not sure it's a realtime kernel.

---

### Post by jpeddicord on 2010-03-27
> **aviramof said:**
> he had asked it in brackets and with a question mark so i'm quite sure he's not sure it's a realtime kernel.

Bingo.

I'm just wondering of there's some sort of medium between what we're using, low-latency, and realtime.

Though again I could be completely wrong. ;)

---

### Post by kurros on 2010-03-27
> **svaens said:**
> Hi , and thanks for the information.

I was wondering. These days, is there any reason not to use the low -latency kernel by default? 

that is; What advantages do we (still) have in using the default non-low-latency kernel ?

thanks!

I believe the preempt kernel disables the idle governor which means the CPU would use more power, but would presumably offer a latency improvement when context switching between several CPU intensive tasks. Also the processor would always be running in "performance" mode and not step down it's frequency.

You can start to see why most users wouldn't want this on a typical desktop (and certainly not a notebook). Someone doing a lot of computational intensive tasks simultaneously might though. This is primarily for a loaded server that is CPU bound and has a reason to reduce latency as much as possible, like a PBX server.

---

### Post by crjackson on 2010-03-27
I would love to see the option during install.  A prompt that would give you a clue as to what it's for, and allows you to select what you want.

I would select an RT or LL Kernel for my desktop, and the generic kernel for my lappy.

---

### Post by Speed_arg on 2010-03-27
So if I don't care about power consumption I should always use a realtime/lowlatency kernel?

---

### Post by Zerp64 on 2010-03-27
> **Speed_arg said:**
> So if I don't care about power consumption I should always use a realtime/lowlatency kernel?

Along with that question, how would an older CPU that doesn't support scaling be utilized with this kind of kernel? I'm sure that any performance increase would be pretty negligible, right?

---

### Post by Ibidem on 2010-03-27
See[ here]("http://linuxtopia.org/online_books/linux_kernel/kernel_configuration/re151.html")                                      for why you might not want the "low-latency" kernel

      PREEMPT_NONE    [Prev]("http://linuxtopia.org/online_books/linux_kernel/kernel_configuration/re150.html")  Chapter 12.  Kernel Configuration Option Reference    [Next]("http://linuxtopia.org/online_books/linux_kernel/kernel_configuration/re152.html")     
      
  
 
  **Name**

 PREEMPT_NONE — No forced preemption (server)
 
    **Description**

  	This is the traditional Linux preemption model, geared toward 	maximizing throughput. It still provides good latency most of the 	time, occasional longer delays are possible. 	
  	Select this option if you are building a kernel for a server or 	scientific/computation system, or if you want to maximize the 	raw processing power of the kernel, irrespective of scheduling 	latencies.

---

### Post by gnomeuser on 2010-03-27
Sadly there are still tons of packaging bugs to work out for this to be actually useful. E.g. one cannot currently use this and the proprietary nvidia driver since that hardcodes a dependency on the -generic kernel, likewise nouveau from xorg-edgers hard depends on -generic while the Lucid version does not.

I have been filing bugs on these issues, but progress is a bit slow.

So yes there is an optional preemptive enabled kernel now but in reality it's not really something you can use yet.

---

### Post by NightwishFan on 2010-03-27
Using DKMS the binary Nvidia driver recompiles for the lowlatency and realtime kernels. I have had it work though in lucid it needs a little struggle.

You are missing the kernel hertz. Fedora and OpenSUSE both ship with 1000hz kernels because of the low latency for interactive desktop use. The lowlatency kernel "currently" primary does this and has a more aggressive preemption. I am planning to use this on a game server.

The realtime kernel tries to do kernel level preemption on some tasks to get a more "realtime" behavior using Ingo Molnar's patches.
[https://rt.wiki.kernel.org/index.php/Main_Page](https://rt.wiki.kernel.org/index.php/Main_Page)

Generally, if you need one of these you already know you need it. You can give the low latency kernel a spin for hardcore gaming or game hosting though. I believe Ubuntu Studio uses the realtime kernel already configured for audio work.

---

### Post by MacUntu on 2010-03-27
Once Lucid goes final I'll update to 2.6.33 and take a look at Con Kolivas' patches ([Phoronix article](http://www.phoronix.com/scan.php?page=news_item&px=ODAxOQ)). Anyone tried them yet? I'm curious if they'll make my systems snappier. :)

---

### Post by NightwishFan on 2010-03-27
There might be a PPA for a CK kernel. I will look around.

---

### Post by NightwishFan on 2010-03-27
Here, for Lucid
[https://launchpad.net/~chogydan/+archive/ppa](https://launchpad.net/~chogydan/+archive/ppa)

I found BFS+BFQ for Karmic here:
[https://launchpad.net/~darxus/+archive/bfsbfq](https://launchpad.net/~darxus/+archive/bfsbfq)

---

### Post by Zerp64 on 2010-03-28
> **NightwishFan said:**
> Here, for Lucid
[https://launchpad.net/~chogydan/+archive/ppa](https://launchpad.net/~chogydan/+archive/ppa)

I found BFS+BFQ for Karmic here:
[https://launchpad.net/~darxus/+archive/bfsbfq](https://launchpad.net/~darxus/+archive/bfsbfq)

Oooh, looks cool. Time to break my system again!

---

### Post by NightwishFan on 2010-03-28
Works for me. :)

---

### Post by zika on 2010-03-28
Works for me, too...
BTW, if I want to have a whole set (generic, preempt, server) of kernels which is the full list of packages I would want to install, i.e. did I omit any that is needed:> ~$ aptitude search linux-ck?
[COLOR=Red]i   linux-ck                                                                                                                                                         - Generic complete Linux kernel.                                                                                                                                             [/COLOR]
p   linux-ck-backports-modules-alsa-lucid-generic                                                                                                                    - Backported drivers for alsa-driver snapshot.                                                                                                                               
p   linux-ck-backports-modules-alsa-lucid-preempt                                                                                                                    - Backported drivers for alsa-driver snapshot.                                                                                                                               
p   linux-ck-backports-modules-alsa-lucid-server                                                                                                                     - Backported drivers for alsa-driver snapshot.                                                                                                                               
p   linux-ck-backports-modules-headers-lucid-generic                                                                                                                 - Backported driver headers for generic kernel image                                                                                                                         
p   linux-ck-backports-modules-headers-lucid-preempt                                                                                                                 - Backported driver headers for preempt kernel image                                                                                                                         
p   linux-ck-backports-modules-headers-lucid-server                                                                                                                  - Backported driver headers for server kernel image                                                                                                                          
p   linux-ck-backports-modules-nouveau-lucid-generic                                                                                                                 - Backported drivers for Nouveau.                                                                                                                                            
p   linux-ck-backports-modules-wireless-lucid-generic                                                                                                                - Backported wireless drivers for generic kernel image                                                                                                                       
p   linux-ck-backports-modules-wireless-lucid-preempt                                                                                                                - Backported wireless drivers for preempt kernel image                                                                                                                       
p   linux-ck-backports-modules-wireless-lucid-server                                                                                                                 - Backported wireless drivers for server kernel image                                                                                                                        
p   linux-ck-crashdump                                                                                                                                               - Linux kernel crashdump setup for the latest generic kernel                                                                                                                 
p   linux-ck-doc                                                                                                                                                     - Linux kernel specific documentation for version 2.6.32                                                                                                                     
[COLOR=Red]i   linux-ck-generic                                                                                                                                                 - Complete Generic Linux kernel                                                                                                                                              [/COLOR]
v   linux-ck-headers                                                                                                                                                 -                                                                                                                                                                            
v   linux-ck-headers-2.6                                                                                                                                             -                                                                                                                                                                            
p   linux-ck-headers-2.6.32-14ck                                                                                                                                     - Header files related to Linux kernel version 2.6.32                                                                                                                        
p   linux-ck-headers-2.6.32-14ck-generic                                                                                                                             - Linux kernel headers for version 2.6.32 on x86/x86_64                                                                                                                      
p   linux-ck-headers-2.6.32-14ck-preempt                                                                                                                             - Linux kernel headers for version 2.6.32 on x86_64                                                                                                                          
p   linux-ck-headers-2.6.32-14ck-server                                                                                                                              - Linux kernel headers for version 2.6.32 on x86_64                                                                                                                          
p   linux-ck-headers-2.6.32-15ck                                                                                                                                     - Header files related to Linux kernel version 2.6.32                                                                                                                        
p   linux-ck-headers-2.6.32-15ck-generic                                                                                                                             - Linux kernel headers for version 2.6.32 on x86/x86_64                                                                                                                      
p   linux-ck-headers-2.6.32-15ck-preempt                                                                                                                             - Linux kernel headers for version 2.6.32 on x86_64                                                                                                                          
p   linux-ck-headers-2.6.32-15ck-server                                                                                                                              - Linux kernel headers for version 2.6.32 on x86_64                                                                                                                          
[COLOR=Red]i   linux-ck-headers-2.6.32-16ck                                                                                                                                     - Header files related to Linux kernel version 2.6.32                                                                                                                        
i   linux-ck-headers-2.6.32-16ck-generic                                                                                                                             - Linux kernel headers for version 2.6.32 on x86/x86_64                                                                                                                      
i   linux-ck-headers-2.6.32-16ck-preempt                                                                                                                             - Linux kernel headers for version 2.6.32 on x86_64                                                                                                                          
i   linux-ck-headers-2.6.32-16ck-server                                                                                                                              - Linux kernel headers for version 2.6.32 on x86_64                                                                                                                          
i   linux-ck-headers-generic                                                                                                                                         - Generic Linux kernel headers                                                                                                                                               
i   linux-ck-headers-preempt                                                                                                                                         - Linux kernel headers for Low Latency Servers.                                                                                                                              
i   linux-ck-headers-server                                                                                                                                          - Linux kernel headers on Server Equipment.                                                                                                                                  [/COLOR]
p   linux-ck-headers-virtual                                                                                                                                         - Linux kernel headers for virtual machines                                                                                                                                  
[COLOR=Red]i   linux-ck-image                                                                                                                                                   - Generic Linux kernel image.[/COLOR]                                                                                                                                                
v   linux-ck-image-2.6                                                                                                                                               -                                                                                                                                                                            
p   linux-ck-image-2.6.32-14ck-generic                                                                                                                               - Linux kernel image for version 2.6.32 on x86/x86_64                                                                                                                        
p   linux-ck-image-2.6.32-14ck-preempt                                                                                                                               - Linux kernel image for version 2.6.32 on x86_64                                                                                                                            
p   linux-ck-image-2.6.32-14ck-server                                                                                                                                - Linux kernel image for version 2.6.32 on x86_64                                                                                                                            
p   linux-ck-image-2.6.32-14ck-virtual                                                                                                                               - Linux kernel image for version 2.6.32 on x86/x86_64                                                                                                                        
p   linux-ck-image-2.6.32-15ck-generic                                                                                                                               - Linux kernel image for version 2.6.32 on x86/x86_64                                                                                                                        
p   linux-ck-image-2.6.32-15ck-preempt                                                                                                                               - Linux kernel image for version 2.6.32 on x86_64                                                                                                                            
p   linux-ck-image-2.6.32-15ck-server                                                                                                                                - Linux kernel image for version 2.6.32 on x86_64                                                                                                                            
p   linux-ck-image-2.6.32-15ck-virtual                                                                                                                               - Linux kernel image for version 2.6.32 on x86/x86_64                                                                                                                        
[COLOR=Red]i   linux-ck-image-2.6.32-16ck-generic                                                                                                                               - Linux kernel image for version 2.6.32 on x86/x86_64                                                                                                                        
i   linux-ck-image-2.6.32-16ck-preempt                                                                                                                               - Linux kernel image for version 2.6.32 on x86_64                                                                                                                            
i   linux-ck-image-2.6.32-16ck-server                                                                                                                                - Linux kernel image for version 2.6.32 on x86_64                                                                                                                            [/COLOR]
p   linux-ck-image-2.6.32-16ck-virtual                                                                                                                               - Linux kernel image for version 2.6.32 on x86/x86_64                                                                                                                        
[COLOR=Red]i   linux-ck-image-generic                                                                                                                                           - Generic Linux kernel image                                                                                                                                                 
i   linux-ck-image-preempt                                                                                                                                           - Linux kernel image for Low Latency Servers.                                                                                                                                
i   linux-ck-image-server                                                                                                                                            - Linux kernel image on Server Equipment.                                                                                                                                    [/COLOR]
p   linux-ck-image-virtual                                                                                                                                           - Linux kernel image for virtual machines                                                                                                                                    
v   linux-ck-kernel-headers                                                                                                                                          -                                                                                                                                                                            
p   linux-ck-libc-dev                                                                                                                                                - Linux Kernel Headers for development                                                                                                                                       
[COLOR=Red]i   linux-ck-preempt                                                                                                                                                 - Complete Linux kernel for Low Latency Servers.                                                                                                                             
i   linux-ck-server                                                                                                                                                  - Complete Linux kernel on Server Equipment.                                                                                                                                 [/COLOR]
p   linux-ck-source                                                                                                                                                  - Linux kernel source with Ubuntu patches                                                                                                                                    
v   linux-ck-source-2.6                                                                                                                                              -                                                                                                                                                                            
p   linux-ck-source-2.6.32                                                                                                                                           - Linux kernel source for version 2.6.32 with Ubuntu patches                                                                                                                 
p   linux-ck-tools                                                                                                                                                   - Linux kernel specific tools for version 2.6.32                                                                                                                             
p   linux-ck-virtual                                                                                                                                                 - Complete Linux kernel for virtual machines                                                                                                                                 
p   linux-crashdump                                                                                                                                                  - Linux kernel crashdump setup for the latest generic kernel  ???

---

### Post by NightwishFan on 2010-03-28
Just install the image and headers for anyone of them that you need.

I just use the generic one since I am on a laptop. You probably do not need the backports and etc.

---

### Post by zika on 2010-03-28
When can we expect 2.6.32-{17,18}...?

Ups, I forgot say: Thank You for this ppa!

---

### Post by plun on 2010-03-28
Nice....:D

Sound was broken at first boot but it was easy fixed....
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

Anyone running with 10000Hz.... ?

---

### Post by NightwishFan on 2010-03-28
100hz is enough for me but I would like to see how that would behave.

---

### Post by plun on 2010-03-28
> One of the patches is BFS, another changes **the default timer frequency to 1000Hz**, another adds new values that allows the timer frequency to be upped to 10,000Hz, and various other changes. 


[http://www.phoronix.com/scan.php?page=news_item&px=ODAxOQ](http://www.phoronix.com/scan.php?page=news_item&px=ODAxOQ)



So default is 1000Hz.... and a preemt kernel should run so.

I cannot figure out howto increase it more....;)

---

### Post by NightwishFan on 2010-03-28
You have to recompile and edit the configuration to allow 10,000hz.

---

### Post by Zerp64 on 2010-03-28
Since we're speaking of customized kernels, can anyone point me to a guide to compiling kernels for Ubuntu, and how to import the standard Ubuntu settings into the kernel being compiled?

Basically I need a tutorial for complete idiots...

---

### Post by NightwishFan on 2010-03-28
For compiling Ubuntu kernels. Really this is just a hobby thing, you will likely see no real gain from doing this. Myself, I have tried it once a long time ago, and never bothered again. I always let someone else do the dirty work.
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Rob2687 on 2010-03-28
I got bored and ran some random benchmarks on the recent kernels. The differences seem pretty minimal in OpenArena. In Gtkperf there was about a 0.1 second improvement on the ck kernel over the Ubuntu kernels.

It'd be nice to see how a 2.6.32.17ck kernel would do.

> **2.6.32-17-generic**
*OpenArena*
840 frames 17.9 seconds 46.8 fps 5.0/21.4/82.0/9.1 ms
840 frames 17.7 seconds 47.6 fps 6.0/21.0/133.0/9.4 ms
840 frames 18.0 seconds 46.6 fps 7.0/21.5/82.0/8.9 ms
840 frames 17.9 seconds 46.8 fps 7.0/21.4/100.0/8.9 ms
840 frames 18.0 seconds 46.7 fps 7.0/21.4/91.0/8.7 ms
[COLOR="Red"]Average: 17.9 seconds 46.9 fps[/COLOR]

*GTKPerf*
Total time:  5.95
Total time:  5.92
Total time:  5.99
Total time:  5.99
Total time:  5.96
[COLOR="Red"]Average:    5.962[/COLOR]


**2.6.32-16ck-generic**
*OpenArena*
840 frames 18.8 seconds 44.8 fps 5.0/22.3/87.0/11.0 ms
840 frames 17.8 seconds 47.1 fps 7.0/21.2/83.0/8.7 ms
840 frames 18.1 seconds 46.5 fps 7.0/21.5/113.0/9.3 ms
840 frames 17.8 seconds 47.2 fps 6.0/21.2/124.0/9.0 ms
840 frames 17.7 seconds 47.5 fps 7.0/21.0/102.0/8.8 ms
[COLOR="Red"]Average: 18.04 seconds 46.62 fps[/COLOR]

*GTKPerf*
Total time:  5.84
Total time:  5.88
Total time:  5.86
Total time:  5.95
Total time:  5.84
[COLOR="Red"]Average:    5.874[/COLOR]


**2.6.32-16-generic**
*OpenArena*
840 frames 18.8 seconds 44.6 fps 5.0/22.4/86.0/11.0 ms
840 frames 17.8 seconds 47.1 fps 8.0/21.2/87.0/9.0 ms
840 frames 18.1 seconds 46.3 fps 8.0/21.6/92.0/9.0 ms
840 frames 17.9 seconds 47.0 fps 7.0/21.3/90.0/8.9 ms
840 frames 17.9 seconds 46.8 fps 7.0/21.3/88.0/8.9 ms
[COLOR="Red"]Average: 18.1 seconds 46.36 fps[/COLOR]

*GTKPerf*
Total time:  5.98
Total time:  5.98
Total time:  5.92
Total time:  5.93
Total time:  5.96
[COLOR="Red"]Average 5.954[/COLOR]

---

### Post by Zerp64 on 2010-03-28
> **NightwishFan said:**
> For compiling Ubuntu kernels. Really this is just a hobby thing, you will likely see no real gain from doing this. Myself, I have tried it once a long time ago, and never bothered again. I always let someone else do the dirty work.
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Yes, I know there wouldn't be much (or any) improvement. I've just wanted to build one for a while but have never gotten around to doing it successfully. I either get too bored to finish or create a faulty kernel. Plus, it's a learning experience.

---

### Post by NightwishFan on 2010-03-28
Indeed it is, have fun with it. I hope it works for you.

---

### Post by zika on 2010-04-13
Today I noticed that 2.6.32-19 versions of ck kernels are available on  ppa:chogydan/ppa. Problem is that, even though I've installed dummy packages that shoul pull the new version when available, they are, still, linked to the old version 2.6.32-16... So, of course, I've removed all the stuff from ppa and installed just one kernel that I wanted to try. It would be nice if the, usual, automatism would work... Kernel, seem to, work nice... Thank You chogydan!

---

### Post by tahina on 2010-04-13
> **Zerp64 said:**
> Since we're speaking of customized kernels, can anyone point me to a guide to compiling kernels for Ubuntu, and how to import the standard Ubuntu settings into the kernel being compiled?

Basically I need a tutorial for complete idiots...

The free Book ["Linux Kernel in a Nutshell"]("http://www.kroah.com/lkn/") by Greg Kroah-Hartman might be of some interest. 

A very late reply and maybe not optimally fitting (not specifically for ubuntu and not for complete idiots), but a great resource non the less...

---

