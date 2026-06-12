---
title: "Dual Core Problem - Tried everything with no luck"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by andrew784 on 2006-11-10
[SIZE="3"]I have a dual core Pentium D processor.  Ubuntu will only recognize and use one of the CPUs.  I have to admit though, that even with just one CPU Ubuntu is a lot faster than XP.  Anyways, I have tried all the different forum advice I found to solve this problem.  Tried initially installing Edgy, but it didn't recognize both CPUs so I formated and installed drapper.  Drapper didn't recognize both cpu's either, so I installed the 686 SMP kernel, restarted, but that still didn't work.  I'm moving over from XP, and in xp both CPU's were recognized and used, so i'm not sure why Ubuntu wont recognize them.  I currently have Ubuntu 6.06 using the 686 SMP Kernel.  Any advice would be greatly appreciated.  Thanks.[/SIZE]

---

### Post by po0f on 2006-11-10
andrew784,

Open up a Terminal (Applications -> Accessories -> Terminal) and enter the following commands:
```
$ uname -a
$ cat /proc/cpuinfo | grep processor
```

---

### Post by M4gg4rd on 2006-11-10
I'm having the same problem on an Ubuntu install using a Pentium Core Duo 2.0 Processor, and the recommended code is bringing back 

bash: $: command not found

Any other suggestions?

---

### Post by yota on 2006-11-10
Hi,

note that you have to write:
```

uname -a

```
and
```

cat /proc/cpuinfo |grep processor

```
without the '$' that's the command prompt!

You'll get something like this:
> 
yota@linbook:~$ uname -a
Linux linbook 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux
yota@linbook:~$ cat /proc/cpuinfo |grep processor
processor       : 0
model name      : Intel(R) Pentium(R) M processor 2.00GHz
yota@linbook:~$


By the way my home machine is a pentium d and both cores were perfectly supported by dapper using smp kernel, and now by edgy with the default 'generic' kernel.

Hope this helps.

---

### Post by M4gg4rd on 2006-11-10
Already attempted that.  Here is what I get in that instance:

> cat /proc/cpuinfo |grep processor
processor       : 0


I'm new to Linux, so sorry if I'm really newbing it up.

Edit:

Just found in another post about updating the Kernel to Linux-686-SMP.  Going that route and well see what happens.

Update:

Same responses in the Terminal and processor unidentified.

I now get this when running the following code: dmesg | grep CPU

> [17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] Initializing CPU#0
[17179572.580000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17179572.580000] CPU: After vendor identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17179572.580000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.580000] CPU: L2 cache: 2048K
[17179572.580000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00000040 0000c1a9 00000000 00000000
[17179572.580000] CPU: Intel Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
[17179575.204000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.204000] ACPI: Processor [CPU0] (supports 8 throttling states)

---

### Post by andrew784 on 2006-11-10
Poof,
Thanks for your response, here is what I got from running the commands
```

andrew@ubuntu:~$ uname -a
Linux ubuntu 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux
andrew@ubuntu:~$ cat /proc/cpuinfo | grep process
processor       : 0
```
It seems that the 686 SMP kernel is installed and being used, but for some reason it still wont recognize both my processors, any further help would be greatly appreciated. ](*,)

---

### Post by M4gg4rd on 2006-11-12
Andrew,

When Ubuntu boots, there is a two-second window in which you can press ESC to enter "Setup".  Inside that, you can choose your Kernel.

Have you selected the Linux-686-SMP via this method?

(I know I'm having problems too, just trying to help you out if you haven't done that)

---

### Post by NorthCoast on 2006-11-12
This is on Edgy?  my Dell laptop shows:
dons@dons-laptop:~$ uname -a
Linux dons-laptop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux
dons@dons-laptop:~$ cat /proc/cpuinfo |grep processor
processor       : 0
processor       : 1

Each processor shows:
model name      : Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz


You might run "dmesg | more" and check what it said about the processors at boot time.

---

### Post by andrew784 on 2006-11-12
M4gg4rd,
Yes I have already tried selecting the 686 smp kernel when booting but unfortunatley that didn't fix the problem.  Thanks for trying to help either way.  If anyone else has any other suggestions, I would greatly appreciate it. :mrgreen:

---

### Post by reazn on 2006-11-12
i had the same issue, 

fixed it by installing the 'generic' kernel.

First thing i naturally did when upgrading to edgy was change the kernel, it turns out you don't need to do that anymore to get a dual core working. :P

---

### Post by andrew784 on 2006-11-12
How do I install the 'generic' kernel?

---

### Post by budman21901 on 2006-11-13
I just went through this same thing upgrading to a smp 686 kernel for my P4 with HT.  I used this thread as a tutorial  [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

After installing i got no entry in grub, and was wondering if everything was correct.  After some research i went to synaptic package manager to check it being installed, and it is installed, but says this:  

"Obsoleted by: linux-image-generic
This package is for upgrades only."

Doing a check i get that it is installed.  

budman@budman-desktop:~$ uname -a
Linux budman-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

Now being a linux newbie of 6 months, i don't know if the generic did it, or my install did it.  Heck, i don't know.  All as i know is i am working, and thirst for more knowledge.  LOL

---

### Post by floke on 2006-11-13
Hi 
Am extreme linux newbie - but also have core duo
My q. is - how do I know if both processors are being recognised?
When running the cat/proc ... thing - I get 2 processors listed - with a 0 on the first and a 1 on the second - like
'processor 0
processor 1'

Is this good or bad?

You have me worried!

Steve

---

### Post by bulldog on 2006-11-13
This is good,you have two processors running :D

---

### Post by andrew784 on 2006-11-13
I still haven't been able to get ubuntu to recognize both of my pentium d cpu's if anyone has any more advice please post.  Here is the output of some commands to give you a better idea of my system:

uname -aandrew@ubuntu:~$ uname -a
Linux ubuntu 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux
andrew@ubuntu:~$ cat /proc/cpuinfo | grep processor
processor       : 0

---

### Post by floke on 2006-11-14
Good to know it works,

Thanks

Steve

---

### Post by pkbarber on 2006-12-14
Interestingly enough my system saw both processors until I installed Beryl.  Has anyone had that problem?  Something tells me that the simplest solution to this problem will be a reinstall... no biggi.

---

### Post by lcaley on 2006-12-14
Ok, I have a different problem from anyone else I've read about. I've installed the 686 kernel for my centrino core duo, but there arent any 686 kernel options in my grub... any ideas??

---

### Post by gunthr on 2006-12-17
@lcaley

My 686 kernel shows up as generic in Grub. A `uname -a` shows it as 686, though.

@all

I have a slightly different issue. I show both processors for my T2500, but they each are only showing up as 1 GHz instead of the 2 GHz they should be. If I boot into the 386 kernel, it shows 1 processor running at 2 GHz. 

uname -a
2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

/proc/cpuinfo shows the correct processor, but only gives each cpu 1000 MHz.

Any ideas?

---

### Post by mcduck on 2006-12-18
In Edgy there is no more specific 686 or k7 or SMP kernels, generic kernel handles them all. Also it handles CPU frequency scaling, which means that if your CPU supports this, the frequency will be scaled down to save power and reduce heat and noise, and when you need more power it'll automatically jump to full speed.

In gnome you can add CPU Frequency Scaling Monitor to your panel to see the speed changing. Right-click on your panel, select 'Add to Panel', find 'CPU Frequency Scaling Monitor' and drag it to your panel.

If you have 2 cores/CPU's add another applet and right-click, go to preferences and set the 'Monitored CPU' to 'CPU 1'. Now you can see how your CPU cores change their frequency depending on what you are doing.

---

### Post by muguwmp67 on 2006-12-18
This REALLY needs to be explained in an easy to find FAQ.  I checked the release notes and all it mentions regarding the kernel is:
Linux 2.6.15.6

If this is a function of the new kernel, it would be good to mention.   It would seem even more so if this is a ubuntu-specific feature.  I've seen several HOW TO's in the forums that mention installing the best kernel for your system in order to improve performance, etc.  and it seems like this is no longer necessary with the generic kernel.

I was having the same problem, and it was due to the generic kernel coming after the 386 kernel in GRUB.  I didn't think much of this because I figured generic meant that it wasn't as good.  Perhaps 'universal' would be better than generic?

A 5:00 am non-sequitur:  
I've been thinking of the following slogan for ubuntu.
"Do you ubuntu too?"
Not sure what it means, but is  5:00 am, I'm tired, and its fun to say.

---

