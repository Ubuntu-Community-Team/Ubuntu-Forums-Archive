---
title: "Ubuntu on a core 2 quad core"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by CGRichyrich on 2011-04-27
If I understand this right, I can get all four cross of the quad core to work as long as I install the 64 bit version of ubuntu?

Sorry if this is a noob question first time installing on a multi core computer

Thanks for the help :P

---

### Post by Buntumatic on 2011-04-27
Yes, and I do not see why you couldn't get it with 32-bit version. 64-bit is better though if you have lots of RAM.

---

### Post by kostkon on 2011-04-27
No :P Thus, you can use the 32bit version, if you like.

You will even get support for >4GB RAM on the 32bit; ubuntu will install the PAE version of the kernel automatically during installation, if you have a large amount of RAM.

---

### Post by dino99 on 2011-04-27
32 or 64 bits dont matter: linux and ubuntu of course works on the core(s) it find, then apps have to be able (programmed) to use these cores.

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

If you have 3 Gb or more of ram, the generic-pae kernel will use it, if your bios is set to use pae of course (there is less conflict/issue with 32 bits)

---

### Post by CGRichyrich on 2011-04-27
So if the system has 4gb of ram or less go with the 32 bit version?

---

### Post by tgm4883 on 2011-04-27
> **dino99 said:**
> 32 or 64 bits dont matter: linux and ubuntu of course works on the core(s) it find, then apps have to be able (programmed) to use these cores.

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

If you have 3 Gb or more of ram, the generic-pae kernel will use it, if your bios is set to use pae of course (there is less conflict/issue with 32 bits)

Um, yea, so that post is dumb (sorry couldn't resist). 

Seriously though, I didn't really get that post. He talks about the hacks that were done to backport 64-bit features to 32-bit processors, but I still don't understand why I shouldn't use 64-bit Ubuntu (other than it might use more ram). He doesn't even talk about the limitations of pae or other issues. 

If anything, that post would make me want to use 64-bit Ubuntu more (I actually already run it on any processor I have that supports 64-bit)

---

### Post by CGRichyrich on 2011-04-27
Well is there any speed increase or any big difference when you are using 32 bit vs 64 bit?

---

### Post by Joe of loath on 2011-04-27
> **CGRichyrich said:**
> Well is there any speed increase or any big difference when you are using 32 bit vs 64 bit?

Yes, according to Phoronix anyway. They see a decent speed increase on things like video transcoding.

---

### Post by tgm4883 on 2011-04-27
> **CGRichyrich said:**
> Well is there any speed increase or any big difference when you are using 32 bit vs 64 bit?

Depends on what you are doing with your PC. I do a lot of encoding, so yea there is a speed increase.

On my netbook though, I doubt there is a speed increase as I don't do much with that machine. It's more of a it's a 64-bit processor, why wouldn't I run a 64-bit OS?

---

### Post by CGRichyrich on 2011-04-27
Well I know I will be playing some world of Warcraft on it and do coding also I would like to add effects to menus and other componets on my desktop so would the 64 bit version be better for me?

---

### Post by Joe of loath on 2011-04-27
> **CGRichyrich said:**
> Well I know I will be playing some world of Warcraft on it and do coding also I would like to add effects to menus and other componets on my desktop so would the 64 bit version be better for me?

Go for it. There are no longer any disadvantages to it (besides some minor fiddling to get flash to work - won't be a problem once flash 10.2 is released, and Ubuntu does it automatically anyway), and there are heaps of advantages.

---

### Post by CGRichyrich on 2011-04-27
Okay cool thank you very much for all the replies !:)

I also had a question of what version ubuntu I should get
Is 11.04 ready?

---

### Post by Dutch70 on 2011-04-27
> **CGRichyrich said:**
> Okay cool thank you very much for all the replies !:)

I also had a question of what version ubuntu I should get
Is 11.04 ready?

10.04 is the current LTS (Long Term Support) supported until April 2013. Probably the most stable also.

10.10 is the latest stable release as of right now. supported until April 2012. Not much different than 10.04 as far as the system goes.

11.04 will be officially released tomorrow. However, there will be almost no difference if you install & update it today, or install it tomorrow. So, yes 11.04 is ready but will probably be buggy for at least a couple months as with any new release, it depends on your hardware. If you want to know for sure, create a live cd or usb stick and select "Try Ubuntu". You should do that regardless of which one you try.

---

### Post by CGRichyrich on 2011-04-27
Okay cool thank you very much for the info ):P

---

