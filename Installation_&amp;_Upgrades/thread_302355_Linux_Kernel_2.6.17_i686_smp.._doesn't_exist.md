---
title: "Linux Kernel 2.6.17 i686 smp.. doesn't exist"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by AquaFox90 on 2006-11-18
I am pretty dissapointed that there's no compiled kernel for 2.6.17 i686 SMP.. I seriously feel the slowness..

Are you guys EVER gonna release it in the repository or should I like the rest of unhappy users compile it manually :/?

---

### Post by ryan on 2006-11-18
If I am not mistaken the generic 2.6.17 kernel will automatically detect a multi core processor and it will work fine, that is what happened with me.

---

### Post by Rhubarb on 2006-11-18
As of Edgy Eft 6.10, the Kernels are now Generic.
I'm currently using 2.6.17-10-generic, it runs just as fast as if there were a 686 version, and it supports SMP too.

I seem to recall some people having issues with the Core 2 Duos, but I'm currently running a Centrino Duo (dual core) chip here.

There's a few threads floating around the forums here addressing exactly your question.
... And I forgot the details of why there's only a generic version, but I do know that it's (almost) pointless having many different versions of the same kernel that all run at the same speed.

I know it's not a very good answer.  The generic kernel shouldn't be too slow for you at all, if it is then perhaps you have a problem somewhere else in your system???

---

