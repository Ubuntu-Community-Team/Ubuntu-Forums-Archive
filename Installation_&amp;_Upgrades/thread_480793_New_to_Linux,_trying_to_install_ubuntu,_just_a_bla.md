---
title: "New to Linux, trying to install ubuntu, just a black screen, please help?"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by bar10dr on 2007-06-21
Hi.

I'm new to Linux and I have heard great things about ubuntu so I thought I'd try it out but I can't even get it to install.

I have a HP pavilion dv9000, AMD Turion 64 x2 processor.

I first tried burning the 64bit cd image and booted it from my laptop, I chose "start or install ubuntu" on the menu, a message pops up "failed to get memory allocation" or something and a progress bar showed up.

Then it shows some text with [OK] on the right side (Some errors regarding a file not found or hardware not found, "bcm43xx_microcode5...") 

Then the screen just goes black.

Tried later with the 32 bit cd and I have the same problem there.

Is ubuntu/linux incompatible with my laptop?

Would apriceate any help, thank you for reading.

Nicolai Linde
Norway

---

### Post by bar10dr on 2007-06-21
Holy crap, now my laptop won't start........ :/

EDIT:

Ok it's up and running again, was a power issue

---

### Post by norrayan on 2007-06-21
have simlar problems with toshiba satellite error messages at start of install then hangs with blank screen after install button pressed this with both 6.5 and 7.04 have you had any luck yet?

---

### Post by bar10dr on 2007-06-21
> **norrayan said:**
> have simlar problems with toshiba satellite error messages at start of install then hangs with blank screen after install button pressed this with both 6.5 and 7.04 have you had any luck yet?

Nope, I cant even start ubuntu when choosing that option..

---

### Post by merlinus on 2007-06-21
Have you tried Safe Mode?  What about the Alternate Desktop install cd, which is text-based and will not have the video problems.

-merlin

---

### Post by Ultra Magnus on 2007-06-21
What graphics card do you have? - When you select install from the list does it show you any errors or anything?

---

### Post by bar10dr on 2007-06-21
> **Ultra Magnus said:**
> What graphics card do you have? - When you select install from the list does it show you any errors or anything?

nvidia, I wrote the error message in my first post.

---

### Post by Ultra Magnus on 2007-06-21
I found this thread that might be of some help:
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)

I also found this:
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29#head-dd3315017e3efc368510f9b2b7022f8aeb15451e](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29#head-dd3315017e3efc368510f9b2b7022f8aeb15451e)

---

### Post by eapache on 2007-06-21
Press F6 to edit the boot options and remove 'splash' and 'quiet'. It should now output a more detailed error message, which should help in the debugging.

---

### Post by bar10dr on 2007-06-22
Fixed the problem.

Pressed F6 at the cd menu and added the word noapic to the boot options, then x booted up without problems.

---

