---
title: "error while running modprobe -v amd76 xrom"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by Eolen on 2006-08-28
Ok, we all start somewhere, and I'm sure you get dozens of idiots a week asking questions like these.

Whenever I try to install Ubuntu onto my second hard drive as a dual boot, I get an error which reads:
error while running modprobe -v amd76 xrom

I get this error a fair way into actually isntalling the operating system (I used the installation's partition wizzard to partition the hard drive and it tells me thats all fine, so i don't think its that). The live CD does actually work, so I am rather perplexed as to what the problem is, not that I know anything about linux in the first place (and i hasten to actually admit im a windows user). I'm running dual AMD 2400+ processors, I've asked somebody who told me this may perhaps be the problem attributed to the error, but I somehow doubt it, because I figure if the OS doesn't like the fact that I have dual cpus, it wouldnt't boot the live cd, which is fine.

I've also tried a copy of fedora which I had lying around, but that erroed out also (can't remember what error that was, didn't have a pen on me at the time). I KNOW you CAN dual boot Ubuntu, and i've asked one or two friends who are savvy, but they have no idea. If anyone can help me out, I'd really appreciate it. 

I'm trying to load Ubuntu 6.0.6

Again, any information at all would be greatly appreciated. If there's any other information i've forgotten to give, i'll answer it as promptly as I can.

Thanks!
I have never really worked with linux before,

---

### Post by hw-tph on 2006-08-28
Try the alternate CD image. While it does not have the fancy graphical environment of the regular livecd it does seem to be a bit more robust (tried and true) and might work where the regular installer CD fails.

Oh, and make sure you have an SMP enabled kernel to make use of both of your processors (not necessary for the installation - deal with that once you're up and running).


Håkan

---

### Post by Eolen on 2006-08-29
I've tried installing it without the pretty pictures ( i actually tried that before the GUI install), I get the same error :(

---

