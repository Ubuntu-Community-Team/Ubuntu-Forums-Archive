---
title: "installed 10.04 but can't load 11.10"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by liberry on 2012-02-16
Hi there! I am super-new to Ubuntu, and I can't help but think I am just missing something. I have built my first new-build and everything works great. Installing 10.04 worked fine and now I have a system that appears to work just fine in every way but one: my graphics card doesn't seem to work too well with 10.04. Everything is wide and bleached out, and I can't choose a decent resolution for my monitor. I can see and read things, but it's unpleasant and certainly not what I should be able to see with a graphics card that has 3D capability.
 
I spent days trying to find drivers that would be compatible with my graphics card, and I really get nowhere. So I asked a friend who is much more knowledgeable than me and he suggested I try a newer version of Ubuntu-- maybe I could find compatible drivers there instead. 
 
I just wanted to try 11.10 to see if it made a difference-- I don't want to download it permanently yet until I'm sure everything else will work too. But I can't get it to load AT ALL. I've tried using the CD, I've tried using the USB. I've tried different discs. I've tried different USBs. Just a black screen with a blinking line in the top left corner. And then that disappears also. The card is an EVGA GeForce GTX 550Ti. 
 
I'd be so grateful if someone could help me sort this out! Thanks in advance.

---

### Post by gordintoronto on 2012-02-16
You went to Ubuntu.com and downloaded Ubuntu 11.10 64-bit, and made sure the download was good?

---

### Post by liberry on 2012-02-16
Yes, and I did it more than once-- my friend gave me his copy already burned to a disk, and since that didn't work, I made my own disk, and when that didn't work, I pulled it onto a USB drive.  
 
When I burned my 10.04 copy, I used the 32 bit version-- I originally burned it for an old machine that quite quickly crapped out and forgot I could have used a 64 bit for the new machine.  Could that be a problem? I hadn't thought about that before.

---

### Post by gordintoronto on 2012-02-16
There are two articles in the Ubuntu Community Documentation which might help you. The first describes common problems with the CD, and is called BootFromCD. The second describes using boot options to handle quirks with your hardware, and is called BootOptions. From what I have seen, one or the other of them solves at least 90% of the problems.

---

### Post by Bucky Ball on 2012-02-16
Have you gotten updates (in 10.04 LTS) and looked in 'Additional Drivers'?

---

### Post by liberry on 2012-02-17
I have indeed gotten the updates and looked for additional drivers. It says none are available. I also went to NVIDIA looking for Linux drivers which they say they have but wouldn't load (which is probably for the best, since I really don't know how well it would have worked.) I've spent a great deal of time digging through the documentation looking for alternatives, but I will look again, just in case. I'm a librarian, so sometimes I overkill the search terms, but I've tried to be general in case I'm missing something by being too specific. 
 
I really appreciate everyone's comments and suggestions! I keep hoping I'll hit on the magic solution. :)

---

### Post by liberry on 2012-02-17
> **gordintoronto said:**
> There are two articles in the Ubuntu Community Documentation which might help you. The first describes common problems with the CD, and is called BootFromCD. The second describes using boot options to handle quirks with your hardware, and is called BootOptions. From what I have seen, one or the other of them solves at least 90% of the problems.
I'm looking at the BootOptions section now, and it's definitely new material for me, so thank you for pointing this out to me!  I'm going to try this tonight.  I hope it works!!

---

### Post by darkod on 2012-02-17
You can try to boot with the nomodeset parameter. Usually this should work with Nvidia.

---

### Post by Bucky Ball on 2012-02-17
> **darkod said:**
> you can try to boot with the nomodeset parameter. Usually this should work with nvidia.

+1.

---

### Post by liberry on 2012-02-18
No modest worked like a charm!  I am so happy!  Thank you.

---

### Post by liberry on 2012-02-18
Ugh!  Autocorrect.  Nomodeset.

---

