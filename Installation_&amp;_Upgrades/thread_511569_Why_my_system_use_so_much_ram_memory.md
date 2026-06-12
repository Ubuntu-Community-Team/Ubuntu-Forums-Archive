---
title: "Why my system use so much ram memory"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by adolfofoliaco on 2007-07-28
hello

I just new at ubuntu and linux but it's  running fine I have a question, when I go to terminal and I use top, the  termina says as follow

top - 00:13:23 up 45 min,  2 users,  load average: 0.47, 0.27, 0.36
Tasks: 115 total,   4 running, 111 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.6%us,  2.0%sy,  0.0%ni, 84.4%id,  0.0%wa,  1.0%hi,  0.0%si,  0.0%st
Mem:   1026240k total,  1002172k used,    24068k free,     9308k buffers
Swap:  3004112k total,    33824k used,  2970288k free,   649264k cached

could some body explain that thank.

Adolfo

---

### Post by encompass on 2007-07-28
That's a tough one to answer...
First off, because you are using alot of memory, it doesn't mean anything bad persay.  Linux likes using more memory sometimes, simply because if you have it you should use it to make your computer run smoother.
You may also want to use top or what ever managerment program you like to see which program is using all the memory.  Java is a BIG hog of memory.  Also some program are buggy and give problems like filling your memory.  These kinds of programs should be avoided.  (Lots of file sharing programs do that.)

---

### Post by davidsrsb on 2007-07-28
Ubuntu, like any othe Linux distribution, uses all memory if run long enough. It caches everything that it can to improve performance and frees ram as required.

Your cpu load is high for a modern machine, which I assume that it is with 1GB ram, most PCs sit at ~1% unless there is some java or flash graphics running

---

### Post by WakkiTabakki on 2007-07-28
A rule of thumb is: unused ram is wasted ram!

As already pointed of, free memory is used for caching stuff. As soon as it's needed for actively running programs, it's freed up, so no worries...
A better measurement is to monitor how much swap is being used. If you comp is swapping a lot, it may indicate something's not right or that you haven't got enough ram...

/N

---

### Post by adolfofoliaco on 2007-07-28
thanks for the quick reply....

---

### Post by WakkiTabakki on 2007-08-02
BTW, here are a few places you can read more about memory and swapping.
** About memory management in Linux
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

** About swappiness (how to control Linux eagerness to swap thing out to disk)
[http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)


/N

---

