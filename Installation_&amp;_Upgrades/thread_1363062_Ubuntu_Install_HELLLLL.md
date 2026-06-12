---
title: "Ubuntu Install HELLLLL"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by haydenangelo on 2009-12-23
Ok, so here's the DL on what's happening.
I built a custom case (yay me, right?)
I downloaded Ubuntu 9.10 for it and burned it to a cd
I boot from the cd (this HDD has no OS), and every thing goes very well until I finish putting in all the info the install asks for.
Then, it just flashes to a black screen, white text, with a crapload of code. 
And freezes.
help plz?

---

### Post by taurus on 2009-12-23
How fast did you burn the CD image?  Try burning it at a slow speed like 4x.

At the first screen, run a check cd for defect to make sure the CD is good before you install it from.

---

### Post by presence1960 on 2009-12-24
I would go back even further in the process.
Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning it to a CD?

If your burning software will not allow you to select burn speed as taurus suggests see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for InfraRecorder.

Once CD is burned as an image boot the CD and at the menu choose "check disk for defects".

If and only if the above conditions are met satifactorily can you use the CD with any certainty.

If all above passes and the problem persists hit F4 at menu and choose safe graphics mode. See [here]("https://help.ubuntu.com/community/BootOptions") for more info on this and other boot options.

BTW what is your gpu (video card)?

---

### Post by haydenangelo on 2009-12-24
It's integrated graphics.
AOpen s651m motherboard.
everything is on board.
Intel 2.66ghz processor
1 gig of ram

---

### Post by haydenangelo on 2009-12-24
UPDATE:
I ran a CheckDisk on the CD I made.
It reboots my computer after about 3 minutes and restarts the CD

---

### Post by presence1960 on 2009-12-24
> **haydenangelo said:**
> UPDATE:
I ran a CheckDisk on the CD I made.
It reboots my computer after about 3 minutes and restarts the CD

Before it reboots the last line near the bottom of screen below the ubuntu logo will tell you if you have any errors or not. You may have to look closely to see the message. Without confirming your Cd has no errors we won't know if the CD is good or not.

---

### Post by presence1960 on 2009-12-24
> **haydenangelo said:**
> It's integrated graphics.
AOpen s651m motherboard.
everything is on board.
Intel 2.66ghz processor
1 gig of ram

what type of integrated graphics? Your mobo docs should tell you. (i.e. Nvidia 6200, ATI or whatever the graphics chip is)

If you don't have the docs you can boot the Live CD and run in terminal lspci. That is a lowercase L in the beginning. Post the output back here.

---

### Post by haydenangelo on 2009-12-24
> **presence1960 said:**
> Before it reboots the last line near the bottom of screen below the ubuntu logo will tell you if you have any errors or not. You may have to look closely to see the message. Without confirming your Cd has no errors we won't know if the CD is good or not.
 
Ok, confirmed that the disc itself is good, zero errors.

---

### Post by haydenangelo on 2009-12-24
> **presence1960 said:**
> what type of integrated graphics? Your mobo docs should tell you. (i.e. Nvidia 6200, ATI or whatever the graphics chip is)
 
If you don't have the docs you can boot the Live CD and run in terminal lspci. That is a lowercase L in the beginning. Post the output back here.
 
 
VGA Compatible controller: Silicon Integrated Systems 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by presence1960 on 2009-12-24
> **haydenangelo said:**
> VGA Compatible controller: Silicon Integrated Systems 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

Ok at the menu when you boot the Live CD to install try hitting F4 and choose safe graphics mode. See [here]("https://help.ubuntu.com/community/BootOptions") for more info.

If that does not work try the alternate text based installer [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by haydenangelo on 2009-12-24
> **presence1960 said:**
> Ok at the menu when you boot the Live CD to install try hitting F4 and choose safe graphics mode. See [here]("https://help.ubuntu.com/community/BootOptions") for more info.
 
If that does not work try the alternate text based installer [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").
 
 
Ok, so, safe graphics mode got me to the partitioning part.
My instructor told me to install it under the EXT3 file system, mount point of "/"
Is that suitable?

---

### Post by CharlesA on 2009-12-24
That should be fine. / is the "root" of the drive.

---

### Post by presence1960 on 2009-12-24
> **charlesa said:**
> that should be fine. / is the "root" of the drive.

+1

---

### Post by haydenangelo on 2009-12-24
Alright, the installation has started (as in, step 6/6 finished)
It took me to the brown screen with the white loading bar and Ubuntu written on it.
Just like using it as the Live CD
Then, it froze :/

---

### Post by presence1960 on 2009-12-24
> **haydenangelo said:**
> Alright, the installation has started (as in, step 6/6 finished)
It took me to the brown screen with the white loading bar and Ubuntu written on it.
Just like using it as the Live CD
Then, it froze :/

I would try it one more time if it freezes again I would try the alternate text based installer.

---

### Post by haydenangelo on 2009-12-24
> **presence1960 said:**
> I would try it one more time if it freezes again I would try the alternate text based installer.
 
 
Thanks a load for your help.
It's 1.19 am here and i'm rather tired.
Gonna give this one more shot then go to bed.
The text based should be done downloading by tomorrow morning

---

### Post by presence1960 on 2009-12-24
> **haydenangelo said:**
> Thanks a load for your help.
It's 1.19 am here and i'm rather tired.
Gonna give this one more shot then go to bed.
***_The text based should be done downloading by tomorrow morning_***
It usually works when the Live CD does not.

---

### Post by haydenangelo on 2009-12-24
> **presence1960 said:**
> It usually works when the Live CD does not.
 
 
Let's hope so.
Thanks again, andddd good night.
I may or may not have to write you again -.-'

---

