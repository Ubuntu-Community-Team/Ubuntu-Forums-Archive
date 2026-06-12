---
title: "Turn off ACPI on live cd"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by XmorgasumX on 2008-07-20
I have an ibm600e and would like to boot in to ubuntu and install it, the bios are from 99.
Help me oh guru's of ubuntu wisdom.

---

### Post by wpshooter on 2008-07-20
Can you tell us a little more about what, if anything, you have done so far ?

---

### Post by XmorgasumX on 2008-07-20
I tried 
noapic
nolapic
pci=irqroute
pci=noacpi
acpi=off
pci=acpi
nolapic
framebuffer=false
linux irqpoll


im new to ubuntu, ive used it before, but im really starting to enjoy it.

---

### Post by wpshooter on 2008-07-20
Why are you trying all of these parameters ?

Are you getting some type of error message when you attempt to boot to the Ubuntu CD and if so, what is the error message ?

Also, have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by XmorgasumX on 2008-07-20
I found it, on i different post.
When i do that i get pci errors and the cd is from ubuntu, i ordered it.

---

### Post by wpshooter on 2008-07-20
> **XmorgasumX said:**
> I found it, on i different post.
When i do that i get pci errors and the cd is from ubuntu, i ordered it.

Because the CD was ordered, does NOT mean that you shouldn't check the integrity.

Does this mean that you have solved your problem ?

---

### Post by XmorgasumX on 2008-07-20
No, not at all i foud the parameters on a differnet post.
And i just checked it, its fine.

---

### Post by wpshooter on 2008-07-20
What type of processor does your computer have ?

How much memory does it have ?

And have you ran memtest on it ?

---

### Post by XmorgasumX on 2008-07-20
it has wither 192 or 256mb, 233 mhz p2. (is what windows said) Memtest says P2 364 mhz
ill do memtest now.

---

### Post by wpshooter on 2008-07-20
It is highly unlikely that you are going to get any version of Ubuntu above Xubuntu to work on this machine and even that is not likely to be a very pleasant experience.

You might try the ALTERNATE CD (as opposed to the Live CD version) from whatever version of Ubuntu you might want to try and have better luck.

I don't think I would even bother with a machine that was earlier than a P3.

---

### Post by XmorgasumX on 2008-07-20
Ohh, my friend said ubuntu would be fine.
i also have a 400mhz gate way that i have to get ubuntu running on.
Any ideas for that?
98 bios.
ACPI error.

---

### Post by wpshooter on 2008-07-20
You need to check out your machines specifications (amount of memory, etc, etc.) against the hardware requirements for whatever version of Ubuntu you may want to try to install.  

Did your friend tell you that there are a fairly goodly number of versions of Ubuntu ?

One of the **KEY** factors in whether Ubuntu is going to install on any particular machine is the amount of memory that it has.  There are also other factors.

---

### Post by XmorgasumX on 2008-07-20
it has 192 mb of ram, 400 mhz
10 gb hdd.
64 mb video card.
what would you suggest, thanks for your time =]

---

### Post by wpshooter on 2008-07-20
If it is to be of the Ubuntu distros, then it would almost have to be **Xubuntu**, installed from the ALTERNATE (text based) CD version.

My suggestion would be Gutsy or you can try Hardy if you are feeling lucky.

---

### Post by XmorgasumX on 2008-07-20
Xubuntu.
Will that get past the acpi errors?

---

