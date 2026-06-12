---
title: "building optimized (arch) packages"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by codenine75a on 2013-12-22
Is this valid to compile optimized packages for my computer architecture?  I want the packages to be compiles with intel core 2 instructions and just not AMD64

```

mkdir playbox
cd playbox
sudo apt-get build-dep xfwm4 firefox
sudo apt-get source xfwm4 firefox --compile --arch-only
sudo dpkg -i *.deb
cd ..
sudo rm -rf playbox

```

---

### Post by grahammechanical on 2013-12-22
I cannot comment on the commands that you are using but I do know that AMD64 is not just for AMD CPUs but also Intel CPUs. I have an Intel Core 2 Duo CPU and I am running Ubuntu installed from a Ubuntu AMD64 ISO image. The instruction sets of Intel and AMD CPUs are compatible. The key difference to watch out for is the difference between 32 bit CPUs and 64 bit CPUs. Although I do not know if this applies in your situation.

Regards.

---

### Post by QIII on 2013-12-22
"AMD64" is a historical convention based on the fact that AMD brought the first hardware with a 64 bit instruction set to the consumer market by a slim margin.  It is not exclusive to AMD products.

You will often see it, but it is becoming more common to use "x86-64" or the like.

---

