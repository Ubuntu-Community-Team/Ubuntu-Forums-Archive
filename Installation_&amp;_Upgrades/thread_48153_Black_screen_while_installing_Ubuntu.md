---
title: "Black screen while installing Ubuntu"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by DeSchurk on 2005-07-11
Hi,
I'm trying to install Ubuntu on my laptop (acer travelmate 4001Lmi with ati mobility radeon 9700). I boot my pc from the installation cd. The "welcome"-screen shows up and i just press enter (regular installation - not the server version). Then, a bunch of letters scroll over the screen and i get.... A totally black screen. Normally i should see a menu where i can select the installation language, but all i see is a black screen. I think it has to do something with the ati-card. But how do i solve this problem ?
I tried the ubuntu live-cd but this also results in a black screen. I think the installation is still active (pressing enter a couple of time awakes the cd-rom drive). But i can't see anything...

Thanks in advance.
(sorry for the bad english)
Greetings from Belgium.

---

### Post by ulgor on 2006-01-25
Hi,
I tried to install the new Ubuntu on my Acer Travelmate 290 with ATI 9700, too... with the same result! The screen just goes black and that's it. The same thing happened with the live CD. After a long time I pressed Enter and finally the Power--button: Live-ubuntu suddenly started! Very strange...

So the live-CD worked somehow, but I still get a black screen with the install CD.

I also tried to turn off everything I found on the forums: Instead of ENTER I typed 
```
linux acpi=off
```

i also tried
```
linux acpi=off noacpi noapic nolapic
```
(without really knowing what i am doing there...)

--> still BLACK SCREEN! That's very frustrating because I already used Ubuntu on my old Desktop PC and I liked it.

---

### Post by DeSchurk on 2006-01-26
Try this:
Connect an external screen to your laptop. If everything goes well, you can install ubuntu on your laptop with the external monitor. When ubuntu is up and running, disconnect the monitor and your problems should be fixed

regards,

---

### Post by ulgor on 2006-01-27
I found a better solution, install with:
```
linux vga=771
```

and if you have problems with the power-saving add some "no"-stuff, I don't know exactly whether it's required... see post above.
```
linux vga=771 acpi=off noapic nolapic
```

Like that I could install Ubuntu without problems!

---

