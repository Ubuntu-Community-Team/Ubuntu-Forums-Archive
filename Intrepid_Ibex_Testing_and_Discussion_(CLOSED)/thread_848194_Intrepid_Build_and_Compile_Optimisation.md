---
title: "Intrepid Build and Compile Optimisation"
date: 2008-07-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-07-03
Hi folks :)

So Ive been thinking about how Ubuntu is build and compile optimisation. I havent been able to find an answer on some questions in this forum so I started an Ubuntu question at:

[https://answers.launchpad.net/ubuntu/+question/37933](https://answers.launchpad.net/ubuntu/+question/37933)

If my question gets answered and there might be a performance benefit to be had for specific arhcitectures and compiler settings Im toying with the idea of getting the source for all used packages and compiling it for top performance.

Ive noticed some make files in MOTU have pre defined optimisations such as -02 but Im not sure about core packages and the overall optimisation of Ubuntu builds, especially on the x64 platform.

---

### Post by kahping on 2008-07-04
Part of your question seems strange. How do you compile for amd64/em64t with i386 optimisations? isn't that pointless since only recent processors are 64bit? is it even possible to do so? 

any 64bit build of Ubuntu would naturally have MMX & SSE optimisations, i think. maybe even SSE2, depending on the supported instruction set of the very first amd64/em64t processor

---

### Post by Nullack on 2008-07-04
What I meant to say was that in x32, it is possible to compile for:

386
486
586
686

etcetc in terms of architecture optimisation

Hence that begs the question with Ubuntu's x64 build, what options are used?

Comparing that to say a user's cat /proc/cpuinfo much show differences that possibly could be used for recompile to make the system faster.

---

### Post by stari4ek on 2008-07-07
-march=native

In case that interpid use gcc 4.3+ you can use this flag. GCC will select best optimization for your cpu, for example for intel core 2 duo it should select -march=core2.

---

### Post by Nullack on 2008-07-07
Thanks, yes 4.3.1 is in Intrepid

Though what is the default Ubuntu packages built too?

Is is possible to query a binary to find out?

---

### Post by stari4ek on 2008-07-07
> **Nullack said:**
> Thanks, yes 4.3.1 is in Intrepid

Though what is the default Ubuntu packages built too?

Is is possible to query a binary to find out?

The main question for me about rebuilding packages was
"How to force apt to choose my locally build binary packages (for example from local repository) instead of same from ubuntu repository"

I wasn't successful with it.

---

### Post by RAOF on 2008-07-07
You probably want to look into the "apt-build" package.  On the other hand, I'm not aware of any benchmarks which suggest that this is a productive use of time ;).

Auto-vectorising is pretty hard, and is already done by hand in many of the places that it'll be useful, anyway.

The benefits of -march= haven't been particularly impressive in the benchmarks I've seen.

---

### Post by stari4ek on 2008-07-07
> **RAOF said:**
> 
Auto-vectorising is pretty hard, and is already done by hand in many of the places that it'll be useful, anyway.

The benefits of -march= haven't been particularly impressive in the benchmarks I've seen.

march flag extend available instructions set (sse/sse2/sse3 for example)

as i know all vectorization stuff performed with -O3 or -ftree-vectorize. this is not march's stuff (but architecture, chosen by mtune, i hope, affect on it)

In any case, without performance tests with real applications I can't say that there will be any advantages of switching from i686 to core2, for example.

---

### Post by RAOF on 2008-07-07
> **stari4ek said:**
> march flag extend available instructions set (sse/sse2/sse3 for example)

as i know all vectorization stuff performed with -O3 or -ftree-vectorize. this is not march's stuff (but architecture, chosen by mtune, i hope, affect on it)
...

Well, not for x86-64, at least.  They *all* support at least SSE1/2/3 :).

And gcc isn't particularly good at auto-vectorising code.  And the places where vectorising would be particularly useful tend to already have vector code explicitly written.

---

### Post by bruce89 on 2008-07-08
> **RAOF said:**
> Well, not for x86-64, at least.  They *all* support at least SSE1/2/3 :).


Not 3.

---

