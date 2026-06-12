---
title: "Installing Windows files with out emulators"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by Liliitha on 2010-04-27
Is it possible to install a program originally meant for Windows without having to go through WINE to do so?  Some of these programs have no Linux support but I wonder if there is still a way to install these programs on Linux, even if it is more difficult.

---

### Post by eveningsky339 on 2010-04-27
I don't think it's possible, hence the very existence of Wine... but I'm no expert on the matter.

---

### Post by eveningsky339 on 2010-04-27
Actually, I did some research, and it looks like a project is under way...

[http://en.wikipedia.org/wiki/Linux_Unified_Kernel](http://en.wikipedia.org/wiki/Linux_Unified_Kernel)

Obviously Ubuntu does not use this kernel, and I cannot in good faith recommend that you attempt to replace the kernel, but this does look promising for future use.

---

### Post by elliotn on 2010-04-28
reading that wiki page and their LUk homepage it sounds interesting.

Bt would this mean viruses and other problems?

---

### Post by xtremesupremacy3 on 2010-06-27
I have been testing the Longene (LUK) project with the new 10.04 support. Unfortunately I ran into considerable problems with my NVidia card and wireless card too, which I wasn't able to solve, I'm still waiting to hear from their support.

The idea is good, basically what it does is that currently, wine translates windows signals into linux ones...kinda, i wont get too technical. But this project allows it to work on a kernel level. This would mean better support for hardware generally accepted only for on Windows. Personally I don't think it would make a world of difference on a software level but I may be wrong. 
As for the core of the question, Wine is the only way (and commercial wine equivelants like Cedega) to allow for some support for Windows programs. You have to see it like this. Linux speaks English, and Windows speaks Chinese, now what Windows says, Linux doesn't understand, and visa versa...Wine is like Google Translate, and a lot of the time it does a good enough job so that Linux understands what the hell Windows is saying, but sometimes it just doesn't work.

Like that? lol

Hope that helps

Arthur

---

