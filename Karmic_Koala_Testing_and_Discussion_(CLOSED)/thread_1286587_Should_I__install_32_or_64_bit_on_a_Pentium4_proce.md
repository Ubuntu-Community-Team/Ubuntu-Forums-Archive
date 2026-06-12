---
title: "Should I  install 32 or 64 bit on a Pentium4 processor?"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dadedo123 on 2009-10-09
My computer supports the 64 bit, but I was just wondering which one will be more stable and faster?

---

### Post by overdrank on 2009-10-09
If your system supports 64bit then you should use 64bit :)

---

### Post by gjoellee on 2009-10-09
I don't think it exists a Pentium 4 64-bit processor. Pentium 4 is a quite old processor.

Install 32bit

---

### Post by dadedo123 on 2009-10-09
> **gjoellee said:**
> I don't think it exists a Pentium 4 64-bit processor. Pentium 4 is a quite old processor.

Install 32bit

But the 64 bit one works well. I'm currently using it.

---

### Post by dino99 on 2009-10-09
64 bits is usefull if you have lot of ram (> 4 gb) or run heavy apps.

---

### Post by dadedo123 on 2009-10-09
I heard that videos in 64 bit are faster. Youtube and flash apps lag a lot in my 64 bit, pentium 4 3.20 Ghz, 1.5 mb ram ddr2. Is there a way to speed up flash? :p

---

### Post by Reiger on 2009-10-09
64bit processors typically offer much more &#8216;goodies&#8217; which 64bit code can take advantage of. One such thing is the higher number of CPU registers and better floating point math (double precision fits in a 64bit register so those registers can be used of which there are already quite a few); and registers are faaast compared to other means of memory access. 

Therefore number crunching performance should be a good bit better on 64bit OS'es and 64bit apps than on 32bit equivalents. Also AMD64 architecture offers some security enhancements over the I386 one which a 64bit OS (kernel, really) can take advantage of. And of course there is the added address space.

Of course for things like video playback nothing beats a good solid video driver stack which supports hardware acceleration of video playback: video cards are essentially nothing but big number crunching platforms; whereas the CPU is designed for much more complex workloads such as those resulting from user-machine-interaction. (Handling a key press is not quite as straightforward as multiplying two numbers.)

---

