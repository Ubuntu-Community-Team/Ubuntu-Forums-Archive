---
title: "Lost RAM"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by nitro_n2o on 2008-08-17
Hi all,

I've recently built a machine with 8 GB's of RAM and it was working perfectly, suddenly I see only ~ 2GB's

I'm running kubnutu 8.04. Does anybody know what is happening? 
I'm not sure what updates were installed on the machine, I appreciate any help

---

### Post by oldos2er on 2008-08-17
Did you check to make sure its seated properly?

---

### Post by nitro_n2o on 2008-08-17
it is not a hardware issue.. I'm sure that the sticks are firmly in place

---

### Post by Pumalite on 2008-08-17
I'd first make sure that the sticks are all well seated on their slots. 2nd I'd do a memtest (8 to 12 HRS).

---

### Post by Kevbert on 2008-08-17
Have you run memtest from the boot menu ?  What does
```
free -m
```
show in Konsole ?

---

### Post by nitro_n2o on 2008-08-17
the memory is fairly new... this happened with two machine so I suspect something else going on

free -m will show 2777 (total) 

i have kubuntu 32 bit edition but the processor support 64-bit by default 
I'm not expert on memory issues

---

### Post by oldos2er on 2008-08-17
> **nitro_n2o said:**
> it is not a hardware issue.. I'm sure that the sticks are firmly in place

 It sure sounds like a hardware issue to me.

---

### Post by Kevbert on 2008-08-17
32 bit operating systems will only show a maximum of 4Gb by default unless you have PIA support enabled in the bios (I believe that's what they call it).  You should run 64 bit Kubuntu to make full use of the memory.

---

### Post by nitro_n2o on 2008-08-17
but the system was showing the full 8GB's 
I'm not sure if some update to the system have messed up something in the kernel 

I don't have physical access to the machine now so I can't mess with bios settings.. is there a way I can fix anything from software

---

### Post by Yesideez on 2008-08-17
I thought 4GB shows up as 3.5GB?

I've got 4GB of RAM installed and Windows XP Pro (32bit) and my Ubuntu (also 32bit) both show 3.5GB free.

---

### Post by cariboo on 2008-08-17
If the same thing happened on two computers with the same ram I would suspect the ram. This problem can not be repaired remotely, you are going to have to be in front of the cpmputer to repair this problem.

Jim

---

### Post by pofigster on 2008-08-17
You know, likely it's a mixture of both the 32bit OS and possibly what your MoBo supports.  Does your MoBo support 8 gigs of ram?  If not you could have fried the bridges and been left with only one 2 gig stick (or whatever).  Additionally, it doesn't't matter if your processor is 64 bit if your OS is 32 bit - the OS is what addresses the RAM, so that's where the bottleneck is.  Why it was showing 8gigs initially, I don't know, but I'd check the MoBo info to make sure 8gigs is OK

---

### Post by Vivaldi Gloria on 2008-08-18
> **Pumalite said:**
> I'd do a memtest (8 to 12 HRS).

How do you do that?

---

### Post by Kevbert on 2008-08-18
> **Yesideez said:**
> I thought 4GB shows up as 3.5GB?

I've got 4GB of RAM installed and Windows XP Pro (32bit) and my Ubuntu (also 32bit) both show 3.5GB free.

The problem with memory not showing up as the full amount is a historic (computer architecture) one.  Originally the computer designers thought that we'd never ever need more than just over 3 Gb of memory.  Above this some memory addresses are used for other peripherals such as ports and drives and therefore this memory isn't used (as it has the same address).  To partly get round this on some PCs you can use the 'memory hole' by allocating new addresses to your RAM (this is performed via the bios). 
It's a bit like the old date problem where dates were calculated from 1900 and not enough memory was allocated to this.

---

### Post by Yesideez on 2008-08-18
Kevbert, thanks for explaining that to me - makes much more sense now.

Just wondering if the OP can remove all the RAM and try one stick at a time, preferably in another machine. That would help eliminate the RAM.

---

### Post by Kevbert on 2008-08-18
> **nitro_n2o said:**
> but the system was showing the full 8GB's 
I'm not sure if some update to the system have messed up something in the kernel 

I don't have physical access to the machine now so I can't mess with bios settings.. is there a way I can fix anything from software

When you first boot up the machine before the Grub menu screen is shown how much memory is displayed ?  You may need to press a key to show the POST screen.  In bios there should also be somewhere where the installed memory is shown.  This will not be changed by an update and the only time this might be changed is if you're running windows, the bios hasn't got write protection enabled and you have a specific type of virus (all three instances).
Again I suggest that you perform a memory test as it is possible that the brand new memory could be faulty.  In the mass production of memory (and all other mass produced items) only a limited number of memory chips will be tested (this is known as batch testing where maybe 1 in 100 devices are fully tested).
It is unlikely that you have been able to use the full 8Gb of installed memory (it has been known, in at least one case, a PC may have a 64 bit processor , but will not run a 64 bit OS).  You really need to run a 64 bit OS and check that all memory can be used.  The OS may even report 8Gb available but will never be able to use more than 4Gb.

---

### Post by hyper_ch on 2008-08-18
> **Kevbert said:**
> unless you have PIA support enabled in the bios (I believe that's what they call it).
PAE --> [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
You can, on Ubuntu, either install the server kernel which has PAE enabled by default or recompile the generic one with PAE support. Then you can use up to 64gb ram on 32bit (which is actually 34bit)

----

As to the problem: Check the motherboard manual how much ram it supports. Then check whether at boot up the bios counts up the whole 8 gb. If it todes, then the problem lies somewhere in the OS.

---

### Post by Pumalite on 2008-08-18
> **Vivaldi Gloria said:**
> How do you do that?

With lots of patience.

---

### Post by sdennie on 2008-08-18
I would make sure you are booting into the -server kernel and not the -generic kernel.  The -generic kernel doesn't have PAE enabled but the -server one does.  Also see: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by Vivaldi Gloria on 2008-08-18
> **Pumalite said:**
> With lots of patience.

Trade secret I guess. :-)

---

### Post by oldos2er on 2008-08-18
> **Vivaldi Gloria said:**
> Trade secret I guess. :-)

 memtest should be available in your grub menu.

---

### Post by nitro_n2o on 2008-08-18
Thanks a lot guys for the all support. 
I'll probably go with a server kernel.. but hopefully that won't break nvidia drivers!! 

The ram is certainly good and working, the motherboard supports up to 16GB's 
I think a recent update of the kernel have disables high memory support 


Thanks!

---

### Post by Vivaldi Gloria on 2008-08-18
> **oldos2er said:**
> memtest should be available in your grub menu.

Oh. OK. Thanks.

---

