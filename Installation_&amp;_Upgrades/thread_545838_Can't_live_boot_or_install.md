---
title: "Can't live boot or install"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by boombah on 2007-09-08
Hi Guys and Girls, i have a problem with the installation of Ubuntu 7.04. 

I have an Acer aspire 5050 which runs Vista home premium very very slowly and i want to set up a dual boot machine. Anyway, i have downloaded the 64bit and the alternative iso and burnt them onto cd. Both will boot to the splash screen and then the problems start. 

64Bit - Click on the install/run live cd , it tries to run and then the cd rom just stops and nothing. 

64Bit Alternate - Select the install from text, it tries to load and i get the error of "soft lockup on CPU#0"

Now i have no idea what to do now, anyone got any ideas?

Thanks

---

### Post by Nebby on 2007-09-08
You could try running a 32 bit installer. Even if it's not what you're after, it'd still be one more thing to know if it works.

---

### Post by banewman on 2007-09-08
First question at this stage is always "what speed did you burn the disk at?" 4x is the fastest speed to burn an ISO if you want it to be reliable. :)

---

### Post by boombah on 2007-09-08
I do not think it is the disk as after i tried those, i tried SUSE that was a proper disk and the same thing happened. It is obviously something to do with this machine but not sure how i can sort out the problem. 

I will have a crack at the 32bit installer later tonight to see what happens.

---

### Post by boombah on 2007-09-09
Tried with the 32 bit installer, now when i click on install it comes up with bios error, the screen goes blank, then stops at the same place. 

Anyone got any more ideas for me?

---

### Post by banewman on 2007-09-10
At the "start or install" prompt hit F6, a command line will appear. Go to the end of the line and type a space then type " noapic nolapic '  - without the quotes and this should get you started.

---

### Post by Pumalite on 2007-09-10
What graphics do you have in your laptop?.

---

### Post by Pumalite on 2007-09-10
This might be your problem:

Gaphics: ATI Radeon Xpress 1100 integrated graphics (64-256mb shared memory)

Maybe you should try Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by boombah on 2007-09-23
Thanks for all the input. Unfortunately i still have had no success. I have done everything that has been suggested. I have now tried 

Ubuntu 6.6 32 bit, 64 bit and alternate. 
Ubuntu 7.04 32 bit, 64 bit and alternate. 
xubuntu alternate.
opensuse 

In all the cd boots, i choose to install from the menu, it gets to the splash screen then about 20 seconds into it just nothing. Splash screen goes. I get different errors on different installs but it is always the same place. Some errors include soft lockup on cpu#0 , bios error and then some i get no error at all. 

I am at a total loss. All of the Ubuntu iso's do work as i have installed on another machine at work.  Any help would be greatly appreciated. 

Thanks

---

