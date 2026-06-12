---
title: "For Ubuntu Developers: Kernel must haves in JJ"
date: 2009-01-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by g29115 on 2009-01-19
After tearing my hair out this weekend with my efforts to add highmem support to my desktop 8.10 system, here are some must haves for future ubuntu releases:

1. Put the kernel config, even for a generic kernel, in the kernel. Store that info so if a person is skilled enough they can compile their own kernel and know what their system is already seeing. 

2. Turn on highmem support by default. Most modern motherboards and systems are coming with 3, 4, and more ram.

B/c of the lack of the two things above I have darn near hosed my system trying to add highmem support by recompiling my kernel. Before anyone tells me that the kernel config is in such and such directory... it wasn't. Couldn't find it.


3. Install kernel development headers and the like from the get go. Everything else under the sun gets turned on and installed, why not these most basic linux tools?

4. Treat the desktop system like a server. Be done with it. The difference are miniscule and the options between the two can be adjust when the person installs the system from the get go. 

I find that Ubuntu (having switched from Slackware) made upkeep of the system and keepings up to date simple and easy. Yay! But when you need to do a simple thing to add a simple feature under the hood you have to go to great lengths and hope something doesn't get screwed up. (I will never understand why reverting back to my old, original kernel, has my video so screwed up). I am no where near and linux expert, even after 10 year or more of use. I would call myself an experienced user. But when my friend, who I would consider and expert/developer/sys admin with over 10 years of experience can't get things to work right then there is a fundamental flaw here. All just so I can use the 8 gigs of ram I have...

---

### Post by jfernyhough on 2009-01-19
When I've used KernelCheck to compile a vanilla kernel it picks up the current config from the running kernel - so it must be there somewhere.

I thought kernel headers /are/ installed by default? They are needed for DKMS after all...

You could use KernelCheck to extract the kernel config, though again, it must be getting it from somewhere. I'm sure I read somewhere about how to extract it - but that was before I started using KernelCheck. :D

However, I'd suggest that if you're trying to add more-than-3.5GB support to a 32-bit kernel use the 64-bit flavour instead. It's designed for high memory systems, after all...

---

### Post by bpl07 on 2009-01-19
I know you didn't want to hear this, but my config and header files are located at /boot/config-2.6.28-4-generic and /usr/src/linux-headers-2.6.28-4-generic, respectively.  [KernelCheck]("http://kcheck.sourceforge.net/download.html") uses these to compile the kernel for you, with the settings you choose using the config file as a starting point.

---

### Post by castrojo on 2009-01-19
> **g29115 said:**
> 1. Put the kernel config, even for a generic kernel, in the kernel. Store that info so if a person is skilled enough they can compile their own kernel and know what their system is already seeing.

These are always in /boot, named something like config-2.6.27-7-generic

> Turn on highmem support by default. Most modern motherboards and systems are coming with 3, 4, and more ram.

I checked my intrepid machines and did a quick straw poll with some friends of mine and they all have HIGHMEM turned on, pretty sure this is the default?

> Before anyone tells me that the kernel config is in such and such directory... it wasn't. Couldn't find it.

That seems odd, I have a year's worth of kernel configs in my /boot and they've always been there.

> All just so I can use the 8 gigs of ram I have...

I spent a few hours once struggling with getting ubuntu to recognize my full 4gb of RAM on my machine and then ended up finding out that the chipset in the box didn't support the full 4gb of RAM, heh...

---

### Post by twright on 2009-01-19
It is probably just simpler to use 64 bit ubuntu if you want more that 4gb of ram

---

### Post by g29115 on 2009-02-13
Thanks to everyone's suggestions and ideas. I want to stay with 32-bit for now. Himem and PAE are enabled in the stock kernel... but it doesn't see the full 8gig for some reason. I know 32-bit seeing all 8gig is possible as the kernel we compiled, (from kernel.org source) with a lot of work did see all the mem. Unfortunately that route broke just about everything else that needed the kernel info for ubuntu. So we are no in the process of reinstalling the system b/c the old sys was so screwed up you couldn't even do ubuntu update properly. Unfortunately we are back to square one in terms of the 8gig prob.

---

### Post by cariboo on 2009-02-13
Have you thought about using the 32bit server kernel, as it is PAE enabled?

Jim

---

### Post by mariner09 on 2009-02-14
Exactly what the previous poster indicated.  It seems like you'd be better off running the server kernel in your situation anyway.

Most of the developers where I work have gone that route except for the poor guys stuck with the T60/T60p that can't use more than 3gb anyway.

---

