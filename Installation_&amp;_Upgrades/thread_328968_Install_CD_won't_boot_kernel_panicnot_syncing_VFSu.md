---
title: "Install CD won't boot: kernel panic/not syncing: VFS/unable to mount root fs"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by Omegatron on 2006-12-31
I have used Ubuntu in the past on my main computer with no problems.  I am trying to install it on my old computer (Thinkpad 600E), but the install CD won't even boot.  

I downloaded this cd: ubuntu-6.10-desktop-i386.iso

It goes to the boot screen fine, and presents the options for "Start or install Ubuntu", etc.  But then when I select one of them (except for memory test), it breaks:

```

[   39.318140] invalid compressed format (err=2)
[   39.323538] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)
[   39.323615]  _

```

Typed from sight.  I have no idea what this means.  Shouldn't it be entirely RAM-based at this point?

---

### Post by xtknight on 2006-12-31
It still has to mount a ram disk.

Did you verify the integrity of your ISO (MD5)?

---

### Post by Omegatron on 2007-01-01
> **xtknight said:**
> Did you verify the integrity of your ISO (MD5)?

Yep.  I had just burned it.  Also I tried a Kubuntu disk which gave the same error.

---

### Post by tommcd on 2007-01-01
Have you tried installing from the alternate CD?
[http://ubuntuforums.org/showthread.php?t=304203&highlight=Thinkpad+600E](http://ubuntuforums.org/showthread.php?t=304203&highlight=Thinkpad+600E)
You will then need to do some work to get the sound going:
[http://ubuntuforums.org/showthread.php?t=94414&highlight=Thinkpad+600E](http://ubuntuforums.org/showthread.php?t=94414&highlight=Thinkpad+600E)
Hope this helps.

---

### Post by Omegatron on 2007-01-01
> **tommcd said:**
> Have you tried installing from the alternate CD?

That worked.  Thanks.

---

### Post by Omegatron on 2007-01-01
That page says my Thinkpad will run faster with the i686 kernel.  Is this really worth the effort?

---

### Post by tommcd on 2007-01-02
Edgy does not use 686 and k7 kernels like Dapper did. Instead it uses a "generic" kernel for 686, k7, and dual core CPUs. Type "uname -r" in terminal to see what kernel you are running. It will be either generic or 386. If you want the generic kernel then install linux-generic from synaptic or "sudo apt-get install linux-generic" from terminal. I have never noticed any difference between the different kernels, but I run the generic kernel (I have an AMD64 CPU) because that is supposed to be optimum for my CPU.
Glad you got it installed. Does the sound work?

---

### Post by Omegatron on 2007-01-02
> **tommcd said:**
> If you want the generic kernel then install linux-generic from synaptic

Ok.  Sounds easy.

> Does the sound work?

Nope.  I followed a few different instructions and nothing worked.  I don't know why there's not just a package you can download that fixes it automatically.

---

### Post by tommcd on 2007-01-03
For the sound issue see this:
[http://ubuntuforums.org/showthread.php?t=282624](http://ubuntuforums.org/showthread.php?t=282624)
Apparently this worked for at least a few people. Give it a try.

---

