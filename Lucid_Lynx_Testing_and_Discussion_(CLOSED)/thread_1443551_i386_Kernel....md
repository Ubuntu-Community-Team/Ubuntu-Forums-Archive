---
title: "i386 Kernel... ?"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Chareos on 2010-03-31
Hi guys,

I just noticed there's a kernel packaged with i386 suffix.

I wonder how it's placed in confrontation with the default kernel, especially for an Atom 270 CPU.

Someone has a hint ? I found nothing so far, except for the basic package description.

---

### Post by jaco223 on 2010-03-31
> **Chareos said:**
> Hi guys,

I just noticed there's a kernel packaged with i386 suffix.

I wonder how it's placed in confrontation with the default kernel, especially for an Atom 270 CPU.

Someone has a hint ? I found nothing so far, except for the basic package description.

Chareos, what bit are you running? 32bit or 64bit system? I think i386 kernel is for the 32bit system.

---

### Post by Chareos on 2010-03-31
Thank you for your reply!

Actually I'm using the default Lucid kernel, on my Atom N270 CPU (which is, afaik, 32bit).

I'm just confused by the other available kernel, with i386 suffix.
The only remarkable difference I can see in their description is "486 or better") in the i386 one.

---

### Post by jaco223 on 2010-03-31
> **Chareos said:**
> Thank you for your reply!

Actually I'm using the default Lucid kernel, on my Atom N270 CPU (which is, afaik, 32bit).

I'm just confused by the other available kernel, with i386 suffix.
The only remarkable difference I can see in their description is "486 or better") in the i386 one.

Chareos, where did you see this kernel? in synaptic? I'm just using the 2.6.32.18 kernel
that installed through update-manager. I originally installed from an alpha 3 released on 
Mar 15th, because the beta 1 release from Mar 18th came with the 2.6.32.20 kernel which
broke my wireless, so I started with kernel 2.6.32.14. I'm using 32bit Lucid.

Edit. I just saw the kernel in synaptic 2.6.32-17, the i386 refers to the architecture of a computer
system, like i686, or amd64. I think i386  and i686 architecture are 32bit.

---

### Post by Chareos on 2010-04-01
Exactly.

But, which one is more suitable for an Atom N270 (first Atom ever released), the default one or the i386 one ?

---

### Post by cariboo on 2010-04-01
The kernel detects what type of cpu you have. I have a Compaq netbook running an atom N270, the kernel sees it as an i686 w/hyper-threading cpu, so the i386 packages are what you need. 

My media center pc with an Atom 320 is detected as an X86_64 w/hyper-threading cpu, so I use X86_64 packages on it.

---

### Post by Chareos on 2010-04-01
So, for my CPU you would suggest me to drop my
2.6.32-18-generic #27-Ubuntu SMP Fri Mar 26 19:51:10 UTC 2010 i686 GNU/Linux
(given by 'uname -a')
and start use the i386 one in the repositories ?

---

