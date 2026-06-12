---
title: "My ACPI Problem Solved - My Experience with installing Ubuntu"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by nixed242 on 2008-01-29
For weeks, I've been trying to install Ubuntu to no avail. I could only get the alternative install to work for me as the Live CD would always hang at the desktop. Even after I was able to install using the text installer, Ubuntu would still freeze on boot for me. After looking through all the forums, I tried all the recommended fixes such as acpi=no, and running X with the vesa driver, both of which got me nowhere. 

I felt that maybe my Linux install problems had something to do with my ATI 9600 Radeon card since ATI doesn't play nicely with Linux. I know that from my days of running Slackware 3 way back when. After a few weeks of giving up, I bought a NVIDIA 7300 GT with 512mb of Ram. I tried installing Linux again, and I still had the same results with the desktop freezing. Somehow, from reading the posts on this forum, I was lead to believe my computer might have a buggy chip set, and that ACPI was the culprit. So why was it that the kernel wasn't accepting my NOACPI variable on boot to make my headache go away? **Somehow it dawned on me to go into my computer's bios, where I found the ACPI setting and disabled it.** Apparently, the Bio setting cancels out any Kernel variables at boot. **The system hasn't frozen or hung at boot since!!!** Here I am in Ubuntu and everything works great!

I don't remember seeing a post on the forum telling people to disable ACPI from inside their BIOS as a fix to this problem, so I figured I'd chronicle my install experience so anyone who has a similar problem getting Ubuntu to work, may solve it the same way I did. It was a real headache, but all is good with the universe now. :)

Now a happy Linux User Once Again,
-Nixed

---

### Post by hal8000 on 2008-01-29
That's a good first post, would you also post your make/model of motherboard, this may help others also.

---

### Post by nixed242 on 2008-01-29
Sorry, I know I forgot some important details in my post.

My Computer -

AMD Athlon 64 2ghz 3200+
FIC K8-800t Motherboard - VIA chipset
2 gigs of DDR Ram
NVIDIA GeForce 7300 GT AGP 512mb video card
running Ubuntu 64 7.10

---

