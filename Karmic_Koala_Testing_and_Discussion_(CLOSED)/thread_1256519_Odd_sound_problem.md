---
title: "Odd sound problem?"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ATPJOE on 2009-09-02
I'm pretty new to Linux, but so far I've been able to work with it easily (I was pretty good with Windows). However, I cannot for the life of me get my sound to work in Ubuntu 9.10 Alpha 4. 
 
It reads my sound card, shows output being produced, but nothing is coming out of the speakers. I've tried disabling the pulse audio, I've checked my cables and whatnot, and I'm going to freak out lol.
 
If someone could walk me through this, I'd really appreciate it. I can post anything needed to ge tthe ball rolling.
 
Thanks.

---

### Post by MoebusNet on 2009-09-02
I'm not an expert by any means, but let me tell you what I found on my Karmic alpha 4. I thought I had your same problem, but by chance I checked the Volume Control in the upper right of the upper Task Bar. It was at full minimum volume! Once I raised the volume, all was well. Cheap and easy, right? If that doesn't help, well sorry about that.

---

### Post by ATPJOE on 2009-09-03
Yeah, I did not forget to check that, it was in-fact the first thing I looked into.
 
I searched and all relevant topics did not lead me in the right direction.

---

### Post by Tompalaz on 2009-09-03
run ```
alsamixer
``` in the terminal and see if you can fix your sound there. 
What soundcard do you have?
I have a Audigy something and I have to enable "Audigy Analog/Digital Output Jack"

On my MacBook however I have to change "channels" (in alsamixer) to 6.

---

### Post by ATPJOE on 2009-09-03
I found a lot of values at zero in alsamixer. And the Audigy Analog/Digital Output Jack is disable, how do you enable it? I'm thinking that would be the problem but I don't know how to enable it.

Thanks, I'm on the right path.



Edit: Nevermind, I got it enabled. Sound works like a charm. Thanks!

---

### Post by ilna on 2009-09-03
In alsamixer use 'm' key for toggling flags.

---

