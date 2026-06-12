---
title: "The kernel for the 386 and 686 version."
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Compucore on 2006-06-15
I just needed to know something here. I am running and old Aptiva from IBM which has a AMD K6-2 400. I was looking at the kernel with the 386 extension and the 686. I don't know off hand if the 686 kernel will work on this processor? Since it is not mentioned for the 686 that it is usable for it? Or should I just stick with the 386 kernel instead?

Compucore

---

### Post by Blitzace on 2006-06-16
You can use 686 if you like (it will work with your processor), but I doubt the performance will increase at all. However ubuntu has a good track record with changing kernels so if you can spare the download bandwidth go for it.

---

### Post by grexk on 2006-06-16
You rather use 686 if you to increase the performance of you cpu.

---

### Post by nico1278 on 2006-06-16
I think you'd better use a kernel coresponding to your computer, AMD -> linux-k7.

---

### Post by awaldram on 2006-06-16
[QUOTE=nico1278]I think you'd better use a kernel coresponding to your computer, AMD -> linux-k7.[/QUOTE]


I wouldn't a K6 is NOT and Athlon I think you'll find it wont boot.

---

### Post by Compucore on 2006-06-16
I would agree with awaldram it is not an Athlon processor its a AMD K6-2 400 It should be an equivilant to a pentium class 1 or Pentium 2 class processor. The reason why I was asking this in the first place was the fact in the notes under the Synaptic packages where they show for the 686 kernel they did not state the AMD K6-2 class processor in the description. Which if they can next time around if they could add this in since it would be some good information. I know it i a minor thing to add it in. But it would be a good thing too since there are basically 2 main processors available right now. I know there are some other cpu's that are still out on the market that are being sold still like the VIA cpu chip. 

Compucore

P.S. Awaldram I will try and add the 686 kernal after I try and find the package that is broken and get it fixed. 

[QUOTE=awaldram]I wouldn't a K6 is NOT and Athlon I think you'll find it wont boot.[/QUOTE]

---

### Post by az on 2006-06-16
I'm pretty sure an amd k6-II will not run either the 686 or k7 kernel.  Use 386.

---

### Post by Compucore on 2006-06-17
Well I did some quick research here. And this is what I had come up with. And here is the link as well for everyone else too to take a look at. [http://www.cpu-world.com/CPUs/CPU.html](http://www.cpu-world.com/CPUs/CPU.html) The AMD K6-2 is a equivilant to a Pentium II class CPU. So the 686 kernel should be fine then.

Compucore :D 

[QUOTE=azz]I'm pretty sure an amd k6-II will not run either the 686 or k7 kernel.  Use 386.[/QUOTE]

---

### Post by az on 2006-06-17
Well, the last time I tried a 686 kernel on an amdk6-II, it would not boot.  I'm pretty sure there are some specific instructions that the pentium has that it doesn't as well as vice versa (3Dnow).

While there are probably the same quality and performance, I don't think that they are the same.

---

