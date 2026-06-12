---
title: "[SOLVED] Preparing for upgrade from 8.04 to 8.10"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by suzypeppercorn on 2008-10-16
I wanted to do a fresh install when 8.10 comes out for one major reason. To install the 64 bit version. Right now i'm running the 32 bit version.

I have a few questions if anyone could help me out.

First, should i install the 64 bit version? What are the major advantages? What if some programs don't come with a 64 bit version? Will 32 bit programs still run?

Second, is there anything i can do to save the setup i have on my machine right now? Would i be able to find a list of all the programs i have installed now and then reinstall them after the fresh upgrade? 8.04 was my first linux distro and i dont have any experience upgrading.

Anyone have experience doing this? Thanks for the help

---

### Post by Abstract Zzzxyz on 2008-10-20
I'm no uber-geek, but the question of running 32 or 64 bit has EVERYTHING to do with your machine. If your computer is a few years old, it's probably 32 bit, newer ones are likely 64. Other than being tailored to one computer or the other, the feel of the OS, and the actual programs are (real geeks please butt it here) probably identical. 

If you're running 32 bit 8.04 on your machine now, I'm sure you've got a 32 bit machine. Running 64 bit won't make your computer faster, it's simply for a different machine.

PLEASE verify this with an actual geek, though. Hope this helps.

Abstract

---

### Post by moliones on 2008-10-20
In synaptic, you can 'Save Markings' (in File menu), and if you check 'Save full state', that will save the status of every package on your system.

However, this will include a lot of things you don't want, like old Kernels from Hardy, packages not in Intrepid, etc. You might want to go through it and only leave the things you specifically want, as dependency management should pull the rest in if you need it when you install. There will probably be a lot of libraries in the list, which should be safe to remove.

(eg eclipse has lots of dependencies, and I don't mind if I have them, so I don't need them in my list, just eclipse, and if it still needs them in Intrepid, they will be installed. Gotta love package management.)

Then, to install all of those things again, just choose the 'Read Markings' option.

Hope this helps.

---

### Post by scientist434 on 2008-10-20
As far as 32-bit or 64-bit the 32 bit will run on pretty much any system even if it is 64-bit. I have the 64-bit version of 8.04 and it runs pretty good some issues with java script for some reason it doesn't like 64-bit. If your worried about compatibility go with 32-bit.

---

### Post by suzypeppercorn on 2008-10-22
i do have a 64 bit machine even though i am running the 32 bit version of 8.04. I guess i will give the 64 bit version of 8.10 and see about the compatibility issues.

I did save the full state markings but my list is so huge it would be impossible to go through. I must have to many programs that i dont use anymore. :)  I will probably just write down all the programs that i use all the time anyway.

Thanks for all the help and answers.

---

