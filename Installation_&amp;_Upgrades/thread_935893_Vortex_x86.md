---
title: "Vortex x86"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by Vadko on 2008-10-02
Hello,

I´ve tried  to install Ubuntu and Xubuntu in a microPC with a vortex86 300mhz processor but its giving me the following error in the installation:

[I]This kernel requires the following features not present on the CPU:
0:0
Unable to boot - please use a kernel appropriate for you CPU.[/I]

Is there a easy way to bypass this? I´m not very savvy in linux.

I´ve read this:
> One way to fix this, is by download and install the kernel manually (using the installer DVD as the temporary OS -- use Rescue mode). But I haven't gone to that path yet.

But I don't quite know how to install a kernel manually.

Any help appreciated

V

---

### Post by tra4d on 2008-12-15
Anybody?  I have the same thing I would like to do.

Thanks,
Scott

---

### Post by caraboy on 2009-04-26
You need to compile a kernel with math-emulation and Cpu type set to 486.

Look at this how-to on how to compile an ubuntu kernel: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Later edit: but please be aware, a vortex 300mhz cpu is quite slow, so you should better start from the server 6.06 install, older but lighter.

---

