---
title: "AMD64 and Intel Processors"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by renomcdonald on 2010-05-10
I have an Intel processor. I can run 64-bit and find it highly advisable for how I use computers. Now the Ubuntu installer says "ubuntu-10.04-desktop-AMD64-iso" does this imply that it can only be installed on AMD processors and not Intel? If so then this would explain why I have sooooo many graphic issues. (GTX 295 coop card)

---

### Post by Gavin77 on 2010-05-10
I'm running 64-bit on an Intel processor, works perfectly.  The filename is kind of confusing that way.

---

### Post by renomcdonald on 2010-05-10
Yea I mean who runs AMD these days anyways? It's obviously a dead end XD

---

### Post by shazbut on 2010-05-10
Nobody with more dollars than sense. ;)
AMD came up with the 64bit x86 instruction set/architecture extensions, so they got to name it, hence AMD64.

---

### Post by efflandt on 2010-05-10
It is called AMD64 because AMD was the first with a working 64-bit chip with those specifications that could also run older 32-bit code.  The original 64-bit Intel chip I think was called IA64 with a different instruction set which could not run 32-bit PC code. AMD64 Linux versions should work with any current Intel 64-bit PC chip that can run a standard Windows version.  I didn't even know that my dual core laptop could run 64-bit Linux until someone mentioned it.  But 64-bit will not run on older hyperthreaded Intel chips that appear to have 2 processors (64-bit will complain that you are attempting to run AMD64 on an i686).

There are other things that could account for video issues. The 10.04 default video is now kernel mode (kms) instead of user mode for some types of video, which can result in issues for some.  I have ATI video, and the default kernel mode video driver breaks suspend and hibernate for me (it hangs with video still on, but blank).  So I need to disable kms in order for suspend and hibernate to work.  Some people have to to that to even boot.

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

---

### Post by renomcdonald on 2010-05-10
hmmmm... I did once fix my issue and got drivers to work but broke the system shortly afterwards. I was too lazy to troubleshoot and retried. It was on kubuntu BTW, I like KDE.

I did get all 3 of my monitors to show while using the nvidia drivers but mousing over to the left screen would freeze the system and cause the mouse to jump between 2 points endlessly. heard of this?

---

### Post by srs5694 on 2010-05-11
> **efflandt said:**
> It is called AMD64 because AMD was the first with a working 64-bit chip with those specifications that could also run older 32-bit code.  The original 64-bit Intel chip I think was called IA64 with a different instruction set which could not run 32-bit PC code.

The Intel Architecture 64 (IA64) chip is also known as *[Itanium.](http://www.intel.com/itcenter/products/itanium/?iid=SEARCH)* Itanium CPUs are still available, and the architecture still has its proponents. My impression is that it's mostly used in fairly high-end servers. IIRC, IA64 CPUs *can* run 32-bit x86 code, but not as well as AMD64 CPUs can. Try Googling "IA64 32-bit" or "Itanium 32-bit" to find information on this topic. You're absolutely right that AMD64 and IA64 are incompatible on the software level (except for their ability to run 32-bit x86 code). There are separate Linux distributions for Itanium. I don't know offhand if there's an Ubuntu for Itanium, but there is a [Debian for IA64.](http://www.debian.org/ports/ia64/)

---

