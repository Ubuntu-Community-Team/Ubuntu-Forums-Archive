---
title: "Please clarify custom kernel approaches"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by krakenfury on 2009-12-02
I've been trying to read and understand as best I can the many threads out there about custom kernel compilation and I'm slowly starting to understand the process.  I think it would help me if someone could clarify the 'make menuconfig' part a little bit.

Should I copy the kernel config file from the existing system or go though the process of selecting all of my hardware from the menu?

I see different approaches to this and I'm going to try to take a stab at why, so please correct me if you see that I'm not understanding.  I fail to see the benefit of copying the existing kernel config file, when the goal of the custom kernel is to streamline the system and get rid of unneeded hardware support.  On the other hand, selecting your hardware from the menuconfig lists is an intimidating task and takes a lot more knowledge of your system than the make and model of your machine's components.  Also, some suggest using your existing config file as a starting place, from which you remove or include things as you see fit.

If my understanding of these approaches is correct, then I have some questions regarding them:

Was the existing config file created at the start of the current boot based on hardware detected by udev or something? or is it loaded up with everything it might need in order to run whatever might be plugged in?

If I need to comb through these lists of hardware choices, where do I start learning all I need to know about my hardware in order to make informed choices.  Is it advisable to use a command like hwinfo or lspci?  Will one or both of these tell you everything you need to know, or will you need to do further research based on what these commands tell you?

I plan to take a stab at a custom kernel when my finals are finished in a couple of weeks, so no rush.  I want to have a very good idea of what I'm doing before I sit down to do this, so any help would be appreciated.

---

