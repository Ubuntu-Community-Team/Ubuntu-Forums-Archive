---
title: "Update 7.10 -&gt; 8.04 w custom kernel?"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by RobbanC on 2008-04-02
Good day

I am about to upgrade some hardware in my home server (everything except the case and a raid cluster). This means that I will also reinstall Xubuntu on my box, which itself is no direct problem.

The situation is this:

* I want to run 8.04 on my box, when it comes out. 
* Either Ubuntu, I have to recompile the kernel to get a hardware raid card to work

->  If I install 7.10 on my box (the current stable Xubuntu), recompile my kernel and the upgrades to 8.04 when it's released, what happens???

->  If I install the 8.04 beta, recompile that kernel and then keeps my system updated, will that work?

->  ...or should I just stay with the 7.10? :rolleyes:

In either way, I assume that my box will work best with the kernel version that comes with the Ubuntu release. (I.e. I can't use an older kernel for a newer Ubuntu)

Help! I'm new to low-level Linux! I have searched my issue, but I can't find anything that I understand.:confused:

---

### Post by blazercist on 2008-04-02
either way i think you will have problems with the raid...

if you install 7.10 and recompile kernel and upgrade to 8.04 you will be wasting time because i believe that hardy has a newer kernel than gutsy which may cause breaky breaky if you try to load hardy with your custom kernel.

if you install 8.04 and recompile you should be ok, as far as keeping your system up to date you just have to beware of kernel updates and make sure not to install them unless they have fixed ur raid problem in that kernel. the problem here is that i dont kno if or how you can install 8.04 or 7.10 for that matter if your raid controller is not recognized... i dont see how you can install the operating system if your harddrives are essentially invisible to the OS.

---

### Post by twright on 2008-04-02
i would just upgrade to the beta first then recompile

---

### Post by RobbanC on 2008-04-02
Thanks!

So, I guess I'm leaning towards the 8.04 beta then.

The raid is indeed a problem while installing. 
I have therefore a separate system disk, and I can later, when I get the raid working, mount the cluster where I want. (simply /raid suits my needs...)

I have tried to install Ubuntu directly on the raid, but I gave up and put in that extra drive... as blazercist said. :)

---

