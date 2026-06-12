---
title: "Error while making kernel 2.6.9"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by Top_se on 2007-07-26
Hello experts!

I`m new to Linux at all, so pls excuse if the following question is very awkward, but I don`t think so. 
I`m testing to build the kernel 2.6.9 on my own. I follow this guide: [http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html) and I used the default .config file of my current kernel 2.6.20-16 to configure the kernel I want to build now, so I think the configuration isn`t the problem.

But after compiling a few lines I received the following error(s):

```
arch/i386/kernel/process.c: In Funktion »show_regs«:
arch/i386/kernel/process.c:252: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »show_trace« unterscheiden sich im Vorzeichenbesitz
{standard input}: Assembler messages:
{standard input}:1389: Error: suffix or operands invalid for `mov'
{standard input}:1391: Error: suffix or operands invalid for `mov'
{standard input}:1739: Error: suffix or operands invalid for `mov'
{standard input}:1741: Error: suffix or operands invalid for `mov'
{standard input}:1851: Error: suffix or operands invalid for `mov'
{standard input}:1852: Error: suffix or operands invalid for `mov'
{standard input}:2023: Error: suffix or operands invalid for `mov'
{standard input}:2025: Error: suffix or operands invalid for `mov'
{standard input}:2193: Error: suffix or operands invalid for `mov'
{standard input}:2206: Error: suffix or operands invalid for `mov'
make[1]: *** [arch/i386/kernel/process.o] Fehler 1
make: *** [arch/i386/kernel] Fehler 2
```

This was the original output, as you can see it`s in German, so I`ll try to translate it into English:

```
arch/i386/kernel/process.c: In function »show_regs«:
arch/i386/kernel/process.c:252: warning: when passing argument 2 from/of (no idea :D) "show_trace" pointertargets differ in ?frontingowning?" 
{standard input}: Assembler messages:
{standard input}:1389: Error: suffix or operands invalid for `mov'
{standard input}:1391: Error: suffix or operands invalid for `mov'
{standard input}:1739: Error: suffix or operands invalid for `mov'
{standard input}:1741: Error: suffix or operands invalid for `mov'
{standard input}:1851: Error: suffix or operands invalid for `mov'
{standard input}:1852: Error: suffix or operands invalid for `mov'
{standard input}:2023: Error: suffix or operands invalid for `mov'
{standard input}:2025: Error: suffix or operands invalid for `mov'
{standard input}:2193: Error: suffix or operands invalid for `mov'
{standard input}:2206: Error: suffix or operands invalid for `mov'
make[1]: *** [arch/i386/kernel/process.o] Error 1
make: *** [arch/i386/kernel] Error 2
``` 

So, I`ve no idea what`s going wrong here ... Is the kernel-version I want to compile buggy, or is it my false?

Thank you a lot for helping me!!!!

---

### Post by kevinlyfellow on 2007-07-26
I wouldn't consider myself an expert, but I'm not sure if using a config file from a newer kernel version to compile an older kernel version is wise.  

Also, did you apply any patches to your kernel?

---

### Post by Top_se on 2007-07-26
> **kevinlyfellow said:**
> I wouldn't consider myself an expert, but I'm not sure if using a config file from a newer kernel version to compile an older kernel version is wise.
Before I used this config-file I tried to config on my own a little bit, but the same error occured.  

> Also, did you apply any patches to your kernel?
I didn`t apply any patches ^^ Is that a mistake?

---

### Post by kevinlyfellow on 2007-07-26
> **Top_se said:**
> Before I used this config-file I tried to config on my own a little bit, but the same error occured.  


I didn`t apply any patches ^^ Is that a mistake?

No, it's safer not to apply patches.  

Maybe you need to use an older version of gcc.
```
sudo apt-get install gcc-3.4
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
```

---

### Post by Top_se on 2007-07-26
> Maybe you need to use an older version of gcc.
```
sudo apt-get install gcc-3.4
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
```
Hm, nice idea but ... I processed the above code successfully but the error doesn`t want to disappear ...

But thx for answering so fast!

---

### Post by Top_se on 2007-07-29
Oh, pls, is there nobody who has got an idea about my problem?

Here I could find a "little help":
[http://aylinux.blogspot.com/2005_11_01_archive.html](http://aylinux.blogspot.com/2005_11_01_archive.html)
But actually I can`t understand the language of the page. I could just find this "patch": 
[http://www.kernel.org/pub/linux/devel/binutils/linux-2.6-seg-5.patch](http://www.kernel.org/pub/linux/devel/binutils/linux-2.6-seg-5.patch) 
from which I got the idea to change two lines in the process.c of my kernel.
Namly I changed those 
```
asm volatile("movl %%fs,%0":"=m" (*(int *)&prev->fs));
asm volatile("movl %%gs,%0":"=m" (*(int *)&prev->gs));
```
into
```
asm volatile("mov %%fs,%0":"=m" (prev->fs));
asm volatile("mov %%gs,%0":"=m" (prev->gs));
```
and when I tried to compile my kernel again the following two errors didn`t appear:
```
{standard input}:2023: Error: suffix or operands invalid for `mov'
{standard input}:2025: Error: suffix or operands invalid for `mov'
``` So I must have fixed them *g* ...
I tried to change the other movl-operation into mov-operation in the process.c file, but this didn`t fix any further errors ...

Maybe this information helps you to help me :D I hope so ...

---

### Post by Top_se on 2007-07-29
k, I got it now, I followed the hole patch and it works now!
I didn`t think, that the patches to the other kernel-files like vm86.c could fix my errors appearing in process.c, but they did ...

So, thx!

---

