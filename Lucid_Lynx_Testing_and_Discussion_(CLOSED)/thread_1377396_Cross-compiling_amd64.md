---
title: "Cross-compiling amd64"
date: 2010-01-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Marshian on 2010-01-10
Hello,

I've got a program written in C++, and an x86_32 Ubuntu 9.10 on my computer. Compiling it for x86_32 is not a problem, but I would like to compile it for x86_64 too. I'm guessing this is easy on an amd64 installation of Ubuntu, but I'd rather not reinstall just to compile one little application.
Is it possible to cross-compile for x86_64 from an x86_32 OS?

Thanks for any responses.

PS: I already tried using a virtual machine, but apparently my CPU doesn't support hardware virtualisation, so I can't run an x86_64 guest :(

---

### Post by xebian on 2010-01-10
> **Marshian said:**
> Hello,

I've got a program written in C++, and an x86_32 Ubuntu 9.10 on my computer. Compiling it for x86_32 is not a problem, but I would like to compile it for x86_64 too. I'm guessing this is easy on an amd64 installation of Ubuntu, but I'd rather not reinstall just to compile one little application.
Is it possible to cross-compile for x86_64 from an x86_32 OS?

Thanks for any responses.

PS: I already tried using a virtual machine, but apparently my CPU doesn't support hardware virtualisation, so I can't run an x86_64 guest :(

Compiling in a 64-bit env is no different than in a 32-bit env.
Unless of course your code is not 100% portable - meaning you have 32-bit calls here and there.

---

### Post by Marshian on 2010-01-10
That's useful to know, but that's not really what I'm looking for. I want to compile for 64-bit from a 32-bit environment...

---

### Post by xebian on 2010-01-10
> **Marshian said:**
> That's useful to know, but that's not really what I'm looking for. I want to compile for 64-bit from a 32-bit environment...

Good luck.

A 64-bit compiler can compile a 32-bit app but a 32-bit compiler can't compile a 64-bit.  A 32-bit compiled app can run in a 64-bit env.

---

### Post by VMC on 2010-01-10
> **Marshian said:**
> Hello,

I've got a program written in C++, and an x86_32 Ubuntu 9.10 on my computer. Compiling it for x86_32 is not a problem, but I would like to compile it for x86_64 too. I'm guessing this is easy on an amd64 installation of Ubuntu, but I'd rather not reinstall just to compile one little application.
Is it possible to cross-compile for x86_64 from an x86_32 OS?


Your in the wrong area. This forum is for Lucid 10.04 testing. Packaging and programing found [**here**]("http://ubuntuforums.org/forumdisplay.php?f=44")

---

### Post by vishalrao on 2010-01-10
Searching for "ubuntu gcc cross compile x86_64 on 32 bit OS" seems to get links to this forum itself if not external info...

I believe you install gcc-multilib and in your compiler flags add " -m64 " and see what happens?

---

### Post by SevenMachines on 2010-01-10
install multilib support for the compiler, this also pulls in the main 64 bit support libraries on x86 ubuntu

$sudo apt-get install g++-multilib

then, for example for the classic 'hello.cpp' example!
$g++ -m64 -o hello hello.cpp

obviously your program may well be more complicated than 'hello!' so you may well need some more of the 64 bit libraries in the repository ( they're most usually named lib64<packagename> )

---

### Post by Marshian on 2010-01-10
> **VMC said:**
> Your in the wrong area. This forum is for Lucid 10.04 testing. Packaging and programing found [**here**]("http://ubuntuforums.org/forumdisplay.php?f=44")

O.o
I'm 100% sure I posted that there :???:
Sorry though, is there a way to move this?

Thanks vishalrao and SevenMachines! That does seem to output something that looks like an executable :)
(And since I can't execute it, it's probably correct too :))

---

