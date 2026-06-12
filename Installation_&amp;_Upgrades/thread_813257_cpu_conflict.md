---
title: "cpu conflict"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by SolaceAvatar on 2008-05-30
When I tried to install Ubuntu, I got the following message: "This kernel requires an x86-64 CPU, but only detected an i686 CPU." I hope it just means I need to download a different file, but... well, not sure what it means.

---

### Post by alguin2 on 2008-05-30
> **SolaceAvatar said:**
> When I tried to install Ubuntu, I got the following message: "This kernel requires an x86-64 CPU, but only detected an i686 CPU." I hope it just means I need to download a different file, but... well, not sure what it means.

What processor do you have? Unless it is an Intel 64 architecture (seems like you have a Pentium), you can't boot with a 64bit Ubuntu.  BTW, I'm not so sure that you'll see a magnitude increase in speed with 64bit Linux. I've tried both versions on my machine 2.2GHz DualCore E2200, and I actually found the 64bit version a bit slower.  I have no benchmarks, but I've read that others have had the same experience.  
The 64bit version's main advantage is that it allows you to access a large address space both in RAM and in disk memory.  If you'll be running a multi-terabyte database, or running simulation programs that require a lot of large integer calculations and huge memory, then the 64bit route is a must.

I've decided to use 32bit Ubuntu, which seems also to have fewer problems. 

Good luck.

---

### Post by SolaceAvatar on 2008-05-30
Oh, so the options are "x64" and "other"? That makes more sense, thanks. I was worried that the processor was too old to run ubuntu...

---

### Post by bammeh on 2008-06-02
I have the same problem

How would I fix this?

---

### Post by PmDematagoda on 2008-06-02
> **bammeh said:**
> I have the same problem

How would I fix this?

You can't use Ubuntu x86_64, so you will have to use the 32-bit version.

---

### Post by bammeh on 2008-06-02
Where can I download this version at?

---

### Post by PmDematagoda on 2008-06-03
> **bammeh said:**
> Where can I download this version at?

Get it from [here]("http://www.ubuntu.com/getubuntu/download"). Choose "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)" and not "64bit AMD and Intel computers".

---

### Post by dsilvia on 2008-11-24
Here, here! Same problem and it appears a lot of folks are having it, not just in this thread/topic but others. ](*,)

See:
[newbie Q: Unable install ubuntu 8.0.4.1 server]("http://ubuntuforums.org/showthread.php?t=905865&highlight=Kernel+Requires+X86-64+detected+i686")

---

### Post by PmDematagoda on 2008-11-24
> **dsilvia said:**
> Here, here! Same problem and it appears a lot of folks are having it, not just in this thread/topic but others. ](*,)

See:
[newbie Q: Unable install ubuntu 8.0.4.1 server]("http://ubuntuforums.org/showthread.php?t=905865&highlight=Kernel+Requires+X86-64+detected+i686")

Please don't resurrect old threads for the purpose of solving a problem, perhaps if you had decided to create a thread of your own, then you may have already solved your problem.

This thread is closed.

---

