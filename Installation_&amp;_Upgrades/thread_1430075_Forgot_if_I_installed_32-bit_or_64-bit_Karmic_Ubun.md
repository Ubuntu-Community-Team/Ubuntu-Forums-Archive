---
title: "Forgot if I installed 32-bit or 64-bit Karmic Ubuntu"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by iClouseau88 on 2010-03-14
Hi,

Some time ago I used a Live Ubuntu CD to fix a multiboot system and now I forgot whether I actually used 32-bit or 64-bit Ubuntu in the original set up.  Is there any command or way to confirm?

Thanks a lot for your help.

---

### Post by srs5694 on 2010-03-15
Several. Perhaps the most reliable is to type "uname -m". You'll see something like this:

```

$ uname -m
x86_64

```

The "x86_64" identifies the kernel as being for the x86-64 architecture -- it's 64-bit. On a 32-bit system, it would read "i686", "i386", or something similar. If you get something ambiguous, try "uname -a". That produces more output, which ought to include an obvious architecture code.

You can also use the "file" command on most binary executable files:

```

$ file /bin/bash
/bin/bash: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```

This identifies the program as being for a 64-bit x86-64 CPU. Note, however, that 64-bit systems can run 32-bit binaries, so if you pick the wrong file, you could mistakenly believe you're running 32-bit when in fact you've got a 64-bit installation. Something basic, like /bin/bash, will ordinarily be in the architecture's native format.

There are also differences in directory layout. On Ubuntu (or at least on my 64-bit Ubuntu 9.10 installation), there are /lib64 and /usr/lib64 symbolic links that point to /lib and /usr/lib, respectively, but these would be absent on 32-bit installations. The 64-bit system also has a /usr/lib32 directory (not a symbolic link) for 32-bit libraries. I don't have a 32-bit Ubuntu system booted at the moment, so I can't be sure, but I'd imagine there would either be or /usr/lib32 directory or it would be a symbolic link to /usr/lib on 32-bit Ubuntu.

---

### Post by adam814 on 2010-03-15
There's always "dpkg --print-architecture" which on your average PC will give either i386 for a 32-bit system or amd64 for a 64-bit system.  Of course if you were on some other architecture (PPC, ARM, etc.) you'd get that too.

---

### Post by mikemelen on 2010-03-15
Open the terminal and type the below command for find the OS  architecture 

#uname -a

---

