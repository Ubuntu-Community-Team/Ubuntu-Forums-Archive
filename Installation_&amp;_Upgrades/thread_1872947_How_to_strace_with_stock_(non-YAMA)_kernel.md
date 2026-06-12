---
title: "How to strace with stock (non-YAMA) kernel?"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by Embedded Linux Guy on 2011-10-31
Hi folks, I am reposting this from Security. I built a 3.1 kernel from Linus' git and it works great, EXCEPT I can't use strace as provided by the strace-4.5.20-2ubuntu2 package. The problem is the strace binary refuses to run unless kernel.yama.ptrace_scope=0, and I don't even have this sysctl variable. So apparently strace defaults to "won't run" in the case of a non-YAMA kernel, instead of "OK fine" which seems more logical.

```
$ strings /usr/bin/strace
attach: ptrace(PTRACE_ATTACH, ...)
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf

```

So, do I need to build my own strace from source, or try to use one from another distro such as debian unstable? Inquiring minds want to know!

Thanks in advance.

---

### Post by MAFoElffen on 2011-10-31
> **Embedded Linux Guy said:**
> Hi folks, I am reposting this from Security. I built a 3.1 kernel from Linus' git and it works great, EXCEPT I can't use strace as provided by the strace-4.5.20-2ubuntu2 package. The problem is the strace binary refuses to run unless kernel.yama.ptrace_scope=0, and I don't even have this sysctl variable. So apparently strace defaults to "won't run" in the case of a non-YAMA kernel, instead of "OK fine" which seems more logical.

```
$ strings /usr/bin/strace
attach: ptrace(PTRACE_ATTACH, ...)
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf

```So, do I need to build my own strace from source, or try to use one from another distro such as debian unstable? Inquiring minds want to know!

Thanks in advance.
I've been testing 3.1 with 12.04 pre-alpha for a month now.  Since current is still in the Release Candidate stage, there still is bugs being worked on.  You know that 3.1~rc10 (and earlier) is in the Ubuntu mailine ppa, right?  RC7 and RC10 seem the most stable so far in my tests.

---

### Post by Embedded Linux Guy on 2011-10-31
> **MAFoElffen said:**
> I've been testing 3.1 with 12.04 pre-alpha for a month now.  Since current is still in the Release Candidate stage, there still is bugs being worked on.  You know that 3.1~rc10 (and earlier) is in the Ubuntu mailine ppa, right?  RC7 and RC10 seem the most stable so far in my tests.

Hi - to clarify, I am running the released v3.1 Linux kernel, with Natty Narwhal (Ubuntu 11.04). The Ubuntu mainline PPA includes Ubuntu patches such as YAMA, which do not exist in the official mainline kernel. I assume you are talking about this kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/)

I am adhering to the process described on this page to build a vanilla stock Linus kernel:

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

For instance if I type

sysctl kernel.yama.ptrace_scope

I get an error, whereas with an Ubuntu-modified kernel you should get some value such as 0 or 1.

---

### Post by matt_symes on 2011-10-31
Hi

> **Embedded Linux Guy said:**
> Hi folks, I am reposting this from Security. I built a 3.1 kernel from Linus' git and it works great, EXCEPT I can't use strace as provided by the strace-4.5.20-2ubuntu2 package. The problem is the strace binary refuses to run unless kernel.yama.ptrace_scope=0, and I don't even have this sysctl variable. So apparently strace defaults to "won't run" in the case of a non-YAMA kernel, instead of "OK fine" which seems more logical.

```
$ strings /usr/bin/strace
attach: ptrace(PTRACE_ATTACH, ...)
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf

```

So, do I need to build my own strace from source, or try to use one from another distro such as debian unstable? Inquiring minds want to know!

Thanks in advance.

EDIT: You responded after i started writing this post and went for a coffee half way through.

I take it this is not a stock Ubuntu kernel you have built. Did you not build yama in ? I was under the impression that it was yama support that stopped processes accessing others memory unless a child process or run as root. I might be wrong on this though as it was a while ago i was originally reading this.

This is from the kernel hardening measures in >10.10. See section ptrace Protection

[https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace%20Protection](https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace%20Protection)

Have you tried

```
echo 0 | sudo tee /proc/sys/kernel/yama/ptrace_scope
```

If this works it will ony work for the current session though. 

You may try create the file

```
sudo nano /etc/sysctl.d/10-ptrace.conf
```

and add

```
kernel.yama.ptrace_scope = 0
```

Kind regards

---

### Post by MAFoElffen on 2011-10-31
> **Embedded Linux Guy said:**
> Hi - to clarify, I am running the released v3.1 Linux kernel, with Natty Narwhal (Ubuntu 11.04). The Ubuntu mainline PPA includes Ubuntu patches such as YAMA, which do not exist in the official mainline kernel. I assume you are talking about this kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1-oneiric/")

I am adhering to the process described on this page to build a vanilla stock Linus kernel:

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

For instance if I type

sysctl kernel.yama.ptrace_scope

I get an error, whereas with an Ubuntu-modified kernel you should get some value such as 0 or 1.
Gotcha...  Title was a clue. 

+1 on Post #4.

Sidenote- Anyone know if Kernel.Org has their bug reporting systems back up yet?  I have bugs at launchpad, that they wanted me to open upstream, but those systems at kernel.org have been down since they were hacked in Sept...

---

### Post by Embedded Linux Guy on 2011-10-31
> I take it this is not a stock Ubuntu kernel you have built. Did you not build yama in ?

Hi, you are correct - by "stock" I mean "stock Linux kernel", not "stock Ubuntu kernel". YAMA exists only in an Ubuntu patch, as far as I can tell. I want to run my system on a clean Linus kernel without Ubuntu-isms, partly for debugging purposes. It is clear from examining the strace binary that it has extraneous YAMA-related code built in, which I would like to get rid of or at least work around.

Thanks for your suggestion though - I did attempt to set the variable anyway, although my kernel does not support it, and just got error messages.

```

jesse@barony:~$ sudo sysctl -w kernel.yama.ptrace_scope=0
[sudo] password for jesse: 
error: "kernel.yama.ptrace_scope" is an unknown key

```

---

### Post by MAFoElffen on 2011-10-31
> **Embedded Linux Guy said:**
> Hi, you are correct - by "stock" I mean "stock Linux kernel", not "stock Ubuntu kernel". YAMA exists only in an Ubuntu patch, as far as I can tell. I want to run my system on a clean Linus kernel without Ubuntu-isms, partly for debugging purposes. It is clear from examining the strace binary that it has extraneous YAMA-related code built in, which I would like to get rid of or at least work around.

Thanks for your suggestion though - I did attempt to set the variable anyway, although my kernel does not support it, and just got error messages.

```

jesse@barony:~$ sudo sysctl -w kernel.yama.ptrace_scope=0
[sudo] password for jesse: 
error: "kernel.yama.ptrace_scope" is an unknown key

```
Just curiosity running amuck in my head at the moment... 

If "yama" does not exist as a module in your kernel...  Logically, when you are asking for or trying to set a "yama" key value, wouldn't "unknown key" be true?  Seems to me that a module parameter won't exist, if the key doesn't exist because the module wasn't included...  Or is that somehow different with "yama."

Am I confused on that?

---

### Post by Embedded Linux Guy on 2011-10-31
> **MAFoElffen said:**
> 
If "yama" does not exist as a module in your kernel...  Logically, when you are asking for or trying to set a "yama" key value, wouldn't "unknown key" be true?

You are correct, this is the expected behavior -- I just wanted to demonstrate that this would not solve my problem.

When I examine strace with strace, it appears that the kernel really is denying this capability -- perhaps using prctl() as described in the KernelHardening document mentioned in #4

[https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace_Protection](https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace_Protection)

If that's the case then maybe there's nothing wrong with my strace binary -- I just have to expect to run strace as root in today's Linux world.

$ strace strace -p 32749
...
ptrace(PTRACE_ATTACH, 32749, 0x1, 0)    = -1 EPERM (Operation not permitted)

---

### Post by MAFoElffen on 2011-10-31
> **Embedded Linux Guy said:**
> You are correct, this is the expected behavior -- I just wanted to demonstrate that this would not solve my problem.

When I examine strace with strace, it appears that the kernel really is denying this capability -- perhaps using prctl() as described in the KernelHardening document mentioned in #4

[https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace_Protection](https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace_Protection)

[COLOR=Red]If that's the case then maybe there's nothing wrong with my strace binary -- I just have to expect to run strace as root in today's Linux world.[/COLOR]

$ strace strace -p 32749
...
ptrace(PTRACE_ATTACH, 32749, 0x1, 0)    = -1 EPERM (Operation not permitted)
Access, rights, permissions-- I think that also means--> So if "only" root or sudo access, then ptrace seems locked down now...

---

### Post by kriegaex on 2012-02-03
Anything new here? I am running Ubuntu 11.10 on colinux, i.e. I cannot just change the kernel because it is part of the colinux VM:

```

$ uname -a
Linux andLinux 2.6.33.7-co-0.7.10-r1588 #1 PREEMPT Mon Aug 8 04:13:31 UTC 2011 i686 athlon i386 GNU/Linux

```

So the problem is as previously described in this thread: I have an Ubuntu version which expects yama to exist in the kernel, but a kernel which just does not have it. I noticed when trying to use [reptyr]("https://github.com/nelhage/reptyr#readme") or [injcode]("https://github.com/ThomasHabets/injcode#readme"). Both of them use ptrace. Strangely enough, the tools still do not work after **[FONT="Courier New"]sudo -i[/FONT].** They do work on my native Ubuntu 11.10 though. But 95% of the time I am on windows, running the colinux VM, so I am stuck here.

Is there any way I can emulate yama so as to satisfy Ubuntu, thinking that is is actually there? I (naively, I am just a user, not a kernel hacker) thought of providing some kind of dummy **[FONT="Courier New"]ptrace_scope[/FONT]**, always returning 0. Is this possible in any way, hacky or not?

---

### Post by Embedded Linux Guy on 2012-02-03
> **kriegaex said:**
> Anything new here? I am running Ubuntu 11.10 on colinux, i.e. I cannot just change the kernel because it is part of the colinux VM:

Well one update is that YAMA is being mainlined. It should already be in linux-next and so hopefully will land in the official tree soon.

[https://lkml.org/lkml/2012/1/18/454](https://lkml.org/lkml/2012/1/18/454)


> Strangely enough, the tools still do not work after **[FONT="Courier New"]sudo -i[/FONT].**

Not cool... I take it this is the same problem where ptrace(2) returns -EPERM? I no longer can reproduce this problem. My suggestion is to build strace yourself from source.

---

