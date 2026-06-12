---
title: "new compiled kernel: boot problems"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by schnee123mann on 2010-06-15
Hello,

I compiled a new Kernel and installed it. When i try to boot the kernel I get the following Message:

```

Ubuntu 10.04

The disk drive for / is not ready yet or not present

Continue to wait; or Press S to skip mounting or M for manual recovery
```When I use the S key, I'm able to log on to a text console. Then I get the following message:
```

Unable to change owner or mode of tty stdin: Read-only file system
```

My /etc/fstab file looks like this:
UUID=xxxxxx    /     ext4     errors=remount-ro    0   1

Does someone have an idea how to fix this problem?

Thank you
Andreas Kasper

---

### Post by darkod on 2010-06-15
Does the previous kernel work OK?

---

### Post by schnee123mann on 2010-06-15
Hi,

yes, the normal (automatically installed from ubuntu) kernel works without any problem.

thank you
Andreas Kasper

---

### Post by renkinjutsu on 2010-06-15
did you remember to compile your filesystem into the kernel? I always miss that and have to compile a second time

---

### Post by darkod on 2010-06-15
It might be simply that the new kernel is not working fine for you.

I recently tried adding 2.6.34 manually also, because it's still not in official update but it should be final version as far as I read, but it had some glitches for me and I didn't even try to investigate.

I just continued using 2.6.32.

---

### Post by renkinjutsu on 2010-06-15
only recently, i've been having consistent problems using the kernel from torvald's git tree. I would just download the tarballs that they have up.

---

### Post by schnee123mann on 2010-06-15
Yes I have compiled the fileystem into the kernel (but the first time i forgot it too ;-).

I compiled the Kernel 2.6.32.2. I need this version because I have to compile a kernel with RTAI ([https://www.rtai.org/](https://www.rtai.org/)) and the patches for RTAI are only available for a few kernel versions.

At the moment I haven't patched the sources. I compiled the original sources from kernel.org

I need RTAI for my master theses at vienna university of technology. So it is really important for me to get the kernel working.

thank you
Andreas Kasper

---

### Post by dino99 on 2010-06-15
goto synaptic, latest rtai is there (maverick 3.80)

---

### Post by schnee123mann on 2010-06-15
hey thank you for the rtai hint ;-)

I found packages @ [http://packages.ubuntu.com/lucid/rtai](http://packages.ubuntu.com/lucid/rtai) but not in synaptic. - I'm using x86_64 and not i386 so that's the reason. 

Do I have to reinstall the system or is there another solution to use the packages?

thank you
Andreas Kasper

---

### Post by dino99 on 2010-06-15
> **schnee123mann said:**
> hey thank you for the rtai hint ;-)

I found packages @ [http://packages.ubuntu.com/lucid/rtai](http://packages.ubuntu.com/lucid/rtai) but not in synaptic. - I'm using x86_64 and not i386 so that's the reason. 

Do I have to reinstall the system or is there another solution to use the packages?

thank you
Andreas Kasper

in fact this package seems to be only 32 bits and thats why i dont use 64 system, too many lack and issue, better to use pae kernel. So if you have room to install a 32 bit pae system you can install rtai.

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by schnee123mann on 2010-06-15
i have a last question,

what do you mean with "pae" kernel?

thank you

---

### Post by schnee123mann on 2010-06-15
The packages listed at [http://packages.ubuntu.com/lucid/rtai](http://packages.ubuntu.com/lucid/rtai) also require a kernel with the rtai patch. - so recompiling the kernel is essential!

I will now try a kernel with the PREEMPT RT Patch, because it is precompiled for ubuntu.

Anyway, the problem with the read-only filesystem isn't solved.


Thank you
Andreas Kasper

---

