---
title: "All seems weird, installation bugs"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by Penguinion on 2011-09-26
Hey!
 
I've had some continuous problems regarding the installation of Ubuntu, from 9 to 11.
 
When I installed 9.4 it told me no new updates where available for the OS, so I decided to transfer the .iso file to a new CD disk, and when i launched it in my computer, the installation seemed very weird, some textures and images where buggy and not exactly how i pictured them, anyways, I managed to install it fine. So when I launch my computer, chosing Ubuntu (I partially have windows XP media edition), it started up and froze at a black screen, showing only the mouse.
 
Help, plax!

---

### Post by mikewhatever on 2011-09-26
9.04 is no longer supported, so the repositories are gone, no wonder you couldn't get updates. The currently supported releases are 10.04, 10.10, 11.04.
To troubleshoot the graphics, post the computer specs.

---

### Post by Penguinion on 2011-10-03
Sorry for answering so late, but I reckon that would be a problem, unfortunately.

Here are my specs!
Processor - AMD Athlon 64 X2 3800+
Chipset - NVIDIA GeForce 6100
Memory - (Unknown manufacturer) 2x512 MB
Video Card - NVIDIA GeForce 9500 GT

Sometime in the future, I'm going to buy a new computer, I just hope this one can coexist with ubuntu, for the time being.

Thanks

Edit:
Sorry for not mentioning, but it was the newest version that I couldn't install ..

---

### Post by 2F4U on 2011-10-03
Try to add nomodeset to the grub2 kernel boot parameters and see if you can start. You probably need to install the proprietary nVidia drivers to get it permanently working.

---

### Post by Penguinion on 2011-10-03
That sounds very promising, although, I'm not sure how to proceed. How do I add the "nomodeset" to the grub2 kernel?

I recognize all the words and commands, but I'm not sure what to do.
 
Thanks

---

### Post by presence1960 on 2011-10-03
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)> **Penguinion said:**
> That sounds very promising, although, I'm not sure how to proceed. How do I add the "nomodeset" to the grub2 kernel?

I recognize all the words and commands, but I'm not sure what to do.
 
Thanks

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Penguinion on 2011-10-04
I ran Ubuntu 11.4 with "nomodeset", worked perfectly! Then I installed the drivers easily with guidance from the os.

Everything works perfectly now! Thanks guys.

---

### Post by mörgæs on 2011-10-04
Good, then please mark the thread 'solved'.

By the way, the name is 11.04 (referring to release in year 2011 and month 04).

---

