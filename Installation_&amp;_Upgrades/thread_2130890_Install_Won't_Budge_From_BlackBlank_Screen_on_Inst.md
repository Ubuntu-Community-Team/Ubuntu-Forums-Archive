---
title: "Install Won't Budge From Black/Blank Screen on Install of 12.04 or 12.10"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by Hunda on 2013-03-30
Hello,

Sorry for the bother, but I am having a few issues installing Ubuntu Server, and/or Desktop, 12.04 and 12.10. I am trying to repurpose an old desktop tower as a home file server by using Ubuntu, however I am unable to get the installation started. Regardless of which option I select at Installation menu, I am met with either a completely black screen, or one with a single white cursor flashing. I have never had any issue installing an previous releases of Ubuntu on different computers, which is why this strikes me as odd.

The computer is a HP Pavillion a465c, Pentium 4 3Ghz, 1 GB RAM, into which I stuck a new, bare, WD 2TB SATA drive (using an IDE to SATA converter). 

Also, please note that I have attempted to select the 'nomodeset' option in 'Other Options' on the install screen.

Any help would be greatly appreciated and Thank you in advance.

---

### Post by Bashing-om on 2013-03-30
Hunda; Hi ! Welcome to the forum.

Let's back up to the barest of basics for a bit.
Can you boot up in the "try ubuntu" mode with the install medium ?
Then make sure that the pentium4 chip supports "pae".
```
cat /proc/cpuinfo
```iirc some of the older p4's did not support "pae"// required for ubuntu 12.04 and up.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by Bucky Ball on 2013-03-30
... further to that; you are certain the IDE to SATA converter is in working order? LTS release advised for a server as has five years support rather than eighteen months and intended for stability for servers and production machines.

---

### Post by Hunda on 2013-03-30
> **Bashing-om said:**
> Hunda; Hi ! Welcome to the forum.

Let's back up to the barest of basics for a bit.
Can you boot up in the "try ubuntu" mode with the install medium ?
Then make sure that the pentium4 chip supports "pae".
```
cat /proc/cpuinfo
```iirc some of the older p4's did not support "pae"// required for ubuntu 12.04 and up.[INDENT=3]
just try'n to help

[/INDENT]


Thank you! It must have been due to this then. I wasn't able to Try without Installing, so I downloaded and burned another image of a different release and at least got further. It got hung up again, but after running the Memory test, it appears the memory is faulty. 

> 
[COLOR=#000000]
... further to that; you are certain the IDE to SATA converter is in working order? LTS release advised for a server as has five years support rather than eighteen months and intended for stability for servers and production machines[/COLOR]



Well I do believe it does. It is recognized in the BIOS, so I assumed it was. Is there a more concise way of knowing?

---

### Post by Bashing-om on 2013-03-30
Hunda;
The present p4 chip may be fine, wont know 'till you are able to boot up something and run some commands to see what is going on. Replace the faulty memory and try and boot again on the liveCD to "try ubuntu". Take it from there.
[INDENT=3]
where there is a will there is a way 
[/INDENT]

---

### Post by Hunda on 2013-03-31
> **Bashing-om said:**
> Hunda;
The present p4 chip may be fine, wont know 'till you are able to boot up something and run some commands to see what is going on. Replace the faulty memory and try and boot again on the liveCD to "try ubuntu". Take it from there.[INDENT=3]
where there is a will there is a way 
[/INDENT]


Hah, you were right. After removing the memory from a faulty slot, the installation on 12.04 proceeded flawlessly. Thank you very much!!

---

### Post by Bucky Ball on 2013-03-31
Good news. You can mark the thread as solved by editing the first post, clicking 'Go Advanced' and changing the prefix to [Solved]. ;)

Enjoy the OS and the learning curve.

---

