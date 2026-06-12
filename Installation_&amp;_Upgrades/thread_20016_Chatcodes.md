---
title: "Chatcodes?"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by Cybermagellan on 2005-03-14
After I tried installing Knoppix/Gnoppix/Slax and Knoppix again I tried Ununtu and was able to install to do so except with a few issues which since I am new to linux I'm kinda having a hard time figuring this out.

1. My computer crashes after a long period of time. Once I caught the kernel saying that the CPU had reached critical temperature 125~ and was shutting down. However my motherboard doesn't have that feature so where this is comming from who knows?

I had tried to install Knoppix and on their forums it says I can try boot=noascpi or something like that to disable the diagnostics. Does this exist in Ubuntu?

2. I have a NVIDIA GeForce 4400 and Ubuntu only recognizes my onboard chip. I downloaded the nVIDIA drivers and it says it can't find the Kernel Packages to install it to? Um, like I said I am new so here are my follow up questions.

         a)Is there an easy way to do this?
         b)The Kernel says it has the Nvidia standard graphics, how do I make 
            those default

I really love ubuntu. And I love Linux. Just ATM it's getting to be more of a pain than I think it can be woth

TIA

Shawn

---

### Post by nocturn on 2005-03-15
About 1
Do you have the exact message?  Do you have lm-sensors installed and configured correctly?

About 2
Try disabling the onboard chip in the BIOS, forcing the system to the Nvidia card.

---

### Post by Cybermagellan on 2005-03-15
[QUOTE=nocturn]About 1
Do you have the exact message?  Do you have lm-sensors installed and configured correctly?

About 2
Try disabling the onboard chip in the BIOS, forcing the system to the Nvidia card.[/QUOTE]
 Um, no I don't have the exact error message...sorry but I think disabling the acpi worked..who knows as of the moment....

I forced back the NVidia card and *groan* that is when all my problems started that now is causing me to install WARTY when I was using 5.0.4 HOARTY? (god I apologize for always wanting to call it horny)

So once I get done installing WARTY then I'll post an update....but who knows I'll probably have the same problem...:-(

---

