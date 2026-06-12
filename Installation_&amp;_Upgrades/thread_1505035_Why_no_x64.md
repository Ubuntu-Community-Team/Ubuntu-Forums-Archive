---
title: "Why no x64?"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by carlbeech on 2010-06-08
Hi Forum,

Ok, up front, please forgive me if I'm being a complete idiot, but can someone tell me why the 64 bit version of ubuntu is only for AMD 64?

I'm running a pentium T3200, which is x64, and I'd like to see how this compares to the 32bit version I'm running now (plus I'd like my machine to use all 4Gb of memory!)

Many thanks

Carl.

---

### Post by dabl on 2010-06-08
OK, you're forgiven.    :lolflag:

Seriously, it has been numerous years since "amd64" referred exclusively to AMD CPUs, in the context of Linux kernel designations.

Read down to "Operating system Compatibility" and "Industry naming conventions" here: [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by carlbeech on 2010-06-08
Ahhhh!

I *knew* I'd be doing something daft! ):P

Many thanks

Carl.

It's what comes of having to make the distinction at work, where we use x64 and itanium 64 machines...  :-)

---

### Post by srs5694 on 2010-06-09
FWIW, "x64" seems to be a Microsoft-ism, or at least that's where it's most commonly used. (I'd never even heard the term until a year or two ago.) AMD originated the current x86-64 architecture, hence "amd64" or "AMD64" being used in many Linux and other open source tools, which began using the architecture before Intel released their first x86-64 CPU. I've still got a fairly early AMD Athlon64 system that predates Intel's first x86-64 release; [I wrote about it for Linux Magazine](http://www.linux-mag.com/id/1699) in 2004. At that time, I used "AMD64" to refer to the architecture because it was the most common term then, and IIRC Intel only announced their first x86-64 CPU as I was writing the piece!

---

### Post by efflandt on 2010-06-10
I also have an early Athlon64 3200+ (2 GHz, 1024K cache) from 2004.  At about the same time I got a comparable 3 GHz Intel at work with Hyperthreading, which appears to be 2 processors, but when I tried to run a 64-bit Ubuntu CD on it, it refused to run 64-bit on an i686.

I didn't even know that my Intel dual core laptop from 2006 could run 64-bit, until I saw it mentioned on these forums, and it works great.

---

### Post by dabl on 2010-06-10
> **efflandt said:**
> 

  At about the same time I got a comparable 3 GHz Intel at work with Hyperthreading, which appears to be 2 processors, but when I tried to run a 64-bit Ubuntu CD on it, it refused to run 64-bit on an i686.



You have to look at the Intel specs for their CPUs, and see whether they are 64-bit architecture.  Intel has changed their terminology over the years, as shown in the wiki article.

Another thing to bear in mind is that the motherboard design, including memory bus, supporting chipset, etc. all has to support 64-bit operation.  Just having the right CPU socket is not automatically sufficient, although most motherboards that will take a 64-bit capable CPU will support it in 64-bit operation.

---

### Post by ngrieb on 2010-08-17
Alright, just got my x64 version of 10.04 up and running, but I had a few questions. I replaced my 32 bit version, but I reformatted before I did so. I wanted to ask what the typical system allocated swap size is because my system is running a bit slow now. I combined the reformatted Linux partitions before I installed because I was not quite sure how the manual partition selector worked. I hope the swap is the only thing slowing this down.

---

