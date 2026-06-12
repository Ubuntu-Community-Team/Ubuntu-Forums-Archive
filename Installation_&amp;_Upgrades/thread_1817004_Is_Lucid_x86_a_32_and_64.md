---
title: "Is Lucid x86 a 32 and 64?"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by sultanf on 2011-08-02
[SIZE=2]Hi everybody; [/SIZE][SIZE=2]if you take a look to: [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

we recognize those two categorizes: >>>>>>
Does the "[/SIZE][SIZE=2]**PC (Intel x86) desktop CD**[/SIZE][SIZE=2]" includes both of x86-32 and x86-64?
I already use that Lucid on core2due and planing to move to i3. I'm asking because "[/SIZE][SIZE=2]**64-bit PC (AMD64) desktop CD**[/SIZE][SIZE=2]" is clearly specifying 64.

[/SIZE][SIZE=2]>>>>>> [/SIZE][SIZE=2]"
**PC (Intel x86) desktop CD**
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.
**64-bit PC (AMD64) desktop CD**
    Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead.
"  thank you

[/SIZE]

---

### Post by FormatSeize on 2011-08-02
I really don't know, and this question has come up somewhere before. I'm not sure if most of these were made during a time when 64 bit architecture was relatively new and only AMD processors had it, or whether there is some other reasoning for this. 

I find it confusing, so I just don't buy AMD processors. Well, that's not the only reason. I will say that I have yet to install an iso that was specifically for 64 architecture processors. I think from the standpoint of a user looking into the monitor, though, there wouldn't be any real visual difference. 

When I'm getting packages, they tend to have this same labeling system. Currently, my processor is 64 capable, but for a person like me that's just saying that I could buy more RAM if I felt like it, or just use it as a 32 bit machine if you don't. So I personally get things that would work fine if I had a single core processor, and use the second core for doing things like compiling programs because I don't feel like staring at scrolling code for 45 minutes. So everything I have is 32 bit, and it seems to work how its supposed to with few problems.

Lastly, I would say that if you need full 32 support for whatever reason, I'd just go with the option that doesn't involve AMD in the name until there's further clarification of what the labels are actually trying to tell us.

---

### Post by garvinrick4 on 2011-08-02
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by oldos2er on 2011-08-02
The AMD64 version is for both Intel and AMD processors. [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by sultanf on 2011-08-03
Thank you all

> **oldos2er said:**
> The AMD64 version is for both Intel and AMD processors. [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

to brief our answer of that article:
"We use AMD64 to refer to all implementations." so, it solved. But ...

as i going to have an i3 Lenovo or Dell, something in that article catch my eyes:
Intel 
[LIST]
[*]F and 5x1 series Pentium 4 using the "Prescott" core 
[*]Pentium D 
[*]Core 2 (Solo, Duo & Quad) 
[*]Core i5 (all) 
[*]Core i7 (all)
[/LIST]
Why they illuminate i3?

---

### Post by oldos2er on 2011-08-03
If you're asking why Core i3 was left out of that list, I don't know; might just be an oversight. Core i3's are 64-bit.

---

