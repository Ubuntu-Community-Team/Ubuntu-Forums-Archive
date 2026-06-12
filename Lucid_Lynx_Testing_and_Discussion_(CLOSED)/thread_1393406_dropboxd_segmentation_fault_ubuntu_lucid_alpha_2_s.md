---
title: "dropboxd segmentation fault ubuntu lucid alpha 2 server?"
date: 2010-01-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by CyberAngel on 2010-01-29
Hello,


I`m trying to install dropbox in a Lucid Lynx alpha 2 server as of the information on the following link.
[http://wiki.dropbox.com/TipsAndTricks/TextBasedLinuxInstall](http://wiki.dropbox.com/TipsAndTricks/TextBasedLinuxInstall)

Every time I run dropboxd binary, I get an instant segmentation fault and an error into /var/log/syslog and /var/log/messages like the following one:

> ...
Jan 29 06:36:05 ubuntu kernel: [ 3275.441897] dropbox[6773]: segfault at 94 ip 0047383c sp bfaf5df4 error 4 in ld-2.11.1.so[469000+1b000]
Jan 29 06:36:06 ubuntu kernel: [ 3276.366489] dropbox[6783]: segfault at 94 ip 002da83c sp bffac134 error 4 in ld-2.11.1.so[2d0000+1b000]
...

Is there any problem with the libc6 package? This .so file is contained into the libc6 package.

As far as I googled, there is no one else mentioning problems with lucid lynx and dropbox that`s why the reason for this post.

Thanks

---

### Post by gmoore777 on 2010-02-07
This isn't much help, but we have a program that is SIGSEGV-ing on LucidLynx Alpha 2 plus updates.
Works fine on HardyHeron. But not LucidLynx. I even installed the older g++/gcc 4.2 on Lucid thinking it was the compiler. No help. We've been looking at the assembler generated, and gdb-ing this small (but not that small) c++ program. I get the feeling that the assembler that gdb is showing me is not the actual code that is being run. and the SIGSEGV is happening on the same "line" of code even while debugging and adding printf() statements. So I don't think we are accidentally writing on the stack. Trying to divide and conquer this c++ file so that I can send it in somewhere as a bug with the compiler, or the kernel, or malloc, etc.
I will look in my logs tomorrow as well and see if I see any messages that may point the finger at the libc6 package or similar. 

Anyways, I just wanted to post my problem on any thread to get some help as well. Sorry for piggybacking on your problem. (they could be related)

---

### Post by pkkid on 2010-02-13
I just installed the Karmic x86 Dropbox on Lucid and it seems to be working fine for me.

---

### Post by CyberAngel on 2010-02-18
> **pkkid said:**
> I just installed the Karmic x86 Dropbox on Lucid and it seems to be working fine for me.

Was it a server installation?
I want to use it without a GUI on a headless server so there is where I had my problem.

---

