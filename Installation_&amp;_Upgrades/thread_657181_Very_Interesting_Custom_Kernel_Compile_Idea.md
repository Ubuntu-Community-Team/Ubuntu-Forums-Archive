---
title: "Very Interesting Custom Kernel Compile Idea"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by family on 2008-01-03
As of Jan 3, 2008 (US); I compiled the the latest stable kernel (2.6.23) using the EXCELLENT guide at ([http://ubuntuforums.org/showthread.php?t=43065&highlight=%5BHOWTO%5D+Compile+your+own+kernel](http://ubuntuforums.org/showthread.php?t=43065&highlight=%5BHOWTO%5D+Compile+your+own+kernel)).  If at any time you wish to compile your own kernel, I highly recommend it.
When I booted into it, I had these problems;
> No sound card support
> Extremely ugly boot-up screen
> No compiz-fusion
> The terminal 'couldn't create child processes' and it would not work at all

but as opposed to the generic Ubuntu kernel I was using, Firefox opened in less than a second as opposed to the 5 seconds it normally takes. Freak coincidence? Perhaps due to the fact the compiz fusion wasn't on? It doesn't matter, it was faster.

If only I could fix those problems, then I could use my own kernel.
My idea is that perhaps some kind genius can create a script that detects your hardware and generates a .config file that the user can feed into the compile process. This way, all the right modules would be loaded (correct hardware support), and all the useless ones could be excluded.
Ideally the script would let the user choose his/her own networking/Wireless/Bluetooth options.
 
For the life of me, I cant find the name of my sound card (lspci, and even the hardware information box in system-pref). Why does the terminal not work? No idea. I know I specified my correct graphics drivers and things, so I dont understand why Compiz Fusion failed. (my computer's all Intel)

If such a script exists can someone please point me to it? thx

---

### Post by leonidas666 on 2008-01-03
I believe at the moment the kernel which is used by ubuntu has almost all drivers compiled as modules. When the computer is booting, then necessary modules are automagically loaded into the kernel.
So by using a kernel which only has the drivers for your particular hardware compiled into the kernel, you could save a little bit of memory (remember, the extra modules from the generic kernel are actually not loaded! It's just that a module will consume a little bit more memory than a compiled-in driver). But you'll have to recompile as soon as you add some hardware to your pc.
Actually, i started with gentoo, and i started with compiling my own super-optimized custom kernel. But then i got fed up with re-compiling whenever i wanted to change something, so in the end i was just using the genkernel-script which i think creates a kernel comparable to the generic kernel used by ubuntu.
To summarize: If you are a expert and really know what you need, then you can go through the make menuconfig thing and do it yourself. But if you are not an expert, you probably don't know what you need, and then the generic kernel is best for you. Even if you are an expert, you might conclude that compiling yourself takes up more of your time than it is worth and still stick with the generic kernel. 
So i think there is not much practical use for a script according to your idea (although it might be a interesting project to create it).
Anyway, is there any special reason why you wanted to compile the kernel yourself?.

---

### Post by family on 2008-01-03
A learning experience (a very headachy one) and to see if there was an actual speed improvement. I honestly believe there is; but it's hard to detect. Perhaps the generic is all anyone needs, after all, that's what it was designed to be :).
The reason anyone compiles something for themselves is probably because they can... And this type of hacking is really common, so I persist that a script that determines your hardware necesities will be useful to a great deal of people, expecially 'newbies' who want an insight into the world of software developmenet. Not only 'newbies', but also advanced users who don't have too much time on their hands that need a quick solution that involves compiling a Linux kernel.
I understand (I think) that most of the drivers unneeded by your computer are modularized, and not loaded. However, suppose I needed to optimize my HDD for free space, no matter how small?

Although this is mostly hypothetical, you can't deny, that hypothetically, it could have **a lot** of applications..

Comments?

---

### Post by 1337455 10534 on 2008-01-04
bump

---

