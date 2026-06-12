---
title: "Cannot boot from desktop AMD64 live CD"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by foxy123 on 2008-09-20
I tried it with Alpha 5 and then with Alpha 6 with the same result. In both case I am stuck on 'Starting powernowd...' 386 version boots fine.

---

### Post by deruberhanyok on 2008-10-26
foxy-

I just tried booting a system with the 64-bit live CD of the release candidate and it stopped booting on the same line.

Anyone know if the "powernowd" is the cause or is the problem somewhere else maybe?

I'm running an Athlon X2 on an M3A79-T Deluxe with 8GB of RAM and a Radeon 4850, if that matters.

---

### Post by daverab on 2008-10-26
I'm having similar issues. It'll get to the first menu, but after that I get a string of lines that include vague things like "panic+0bx4/0x171" and ends with end trace. Seems like the kernel is taking a dump.

I've also tried the latest build cd (10/24) with the same problem. If I could remember the no acpi and other debug lines I'd try those options. I'm trying to look them up now.

And yes, I know I can use 64 bit, I'm on Vista 64bit right now.


More info:

Using the Gigabyte S3 board (solid caps) with the AMD 770 SB600 combo. Nvidia 7600GT card

I have been able to run i386 no problem (not an install though, upgraded from Hardy...redid partitions because of Vista 64-bit purchase).

---

### Post by deruberhanyok on 2008-10-26
I just happened to connect a hard drive from another system that has the Intrepid beta (32-bit) on it. That works fine... so I'm feeling certain that the issue is specific to the 64-bit version.

---

### Post by Kevbert on 2008-10-26
This seems to be a common problem, just go to [https://bugs.launchpad.net/bugs/+bugs?field.searchtext=powernowd&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=powernowd&search=Search+Bug+Reports&field.scope=all&field.scope.target=) and you'll see that a large number of bugs have been filed. Bug 267198 seems to match what all of you are saying. If you all add a comment to that maybe someone will be prompted into looking into it.

---

### Post by foxy123 on 2008-10-26
It is not just that. I installed the alpha using the alternative CD and then removed powernowd. I think the problem is with cpu frequency scaling but it looks like now one knows what it is. You can also add noapic and acpi=off in your boot options.

---

### Post by deruberhanyok on 2008-10-28
Foxy, what kind of processor do you have? I just noticed that both myself and daverab both have AMD chips... is yours also AMD?

I'm wondering if we can find some kind of common piece of hardware that might help to figure it out. Obviously the problem isn't happening for everyone, so for those of us who get this... what processor/motherboard do you have?

[edit] - is it the laptop in your specs? One of those last gen P4s that supported 64-bit? Or a different box?

---

### Post by foxy123 on 2008-10-28
> **deruberhanyok said:**
> Foxy, what kind of processor do you have? I just noticed that both myself and daverab both have AMD chips... is yours also AMD?

I'm wondering if we can find some kind of common piece of hardware that might help to figure it out. Obviously the problem isn't happening for everyone, so for those of us who get this... what processor/motherboard do you have?

[edit] - is it the laptop in your specs? One of those last gen P4s that supported 64-bit? Or a different box?

yes, it's laptop in my signature. My PC is AMD based: 
Processor: AMD Athlon 64 X2 3800+
Mobo: ECS K8 NVIDIA -Socket 939 (K51150) NFORCE4-A939 ATX

---

### Post by deruberhanyok on 2008-10-28
Hmm. It happens on both of them? Here I was thinking it might be related to this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/111375](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/111375)

---

### Post by foxy123 on 2008-10-29
> **deruberhanyok said:**
> Hmm. It happens on both of them? Here I was thinking it might be related to this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/111375](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/111375)

no, no. The laptop is run on 32bit Xubuntu.

I am not sure about this bug, though it might be related. As I remember cpuinfo does not identify the kernel at all in my case.

---

### Post by deruberhanyok on 2008-10-29
Ah, alright, sorry about the confusion there.

Is anyone else having this issue with an Athlon 64 or X2 system running 64-bit? Looks like the processor is the only thing that we have in common so far.

---

