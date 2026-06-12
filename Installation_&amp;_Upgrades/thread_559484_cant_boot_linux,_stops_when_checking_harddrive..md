---
title: "cant boot linux, stops when checking harddrive."
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Fyksen on 2007-09-25
Hello, I`m new with Linux and Ubuntu.
I have a HP PAVILION DV 9074ea

Speccs:
Prosessor: AMD Turion 64 X2
Prosessorspeed: 1600 MHz
Ram: 2x512
Hardrive #1: 80 GB
Hardrive #2: 80 GB
grafick card: NVIDIA GeForce Go 7600


I tried to install ubuntu 86x from a alternative cd. (ubuntu 7.04)
Everything went perfectly until I was going to start Ubuntu after the installation.
Then the computer "popd" out from it`s bootscreen, and into a text "loader".

Then it stood:
/dev/sdb1 has gone 49710 days without being cheked, check forced.

Then the check pops right into 15, 21 og 18% before it stops, and then nothing more happens, it just stands there. I`ve tried many times.

I`m not very good in english, and I`m new to ubuntu, so please help me step by step :) .

I use dualboot btw, Windows vista businiss on the other partision.

---

### Post by callan79 on 2007-09-25
> **Fyksen said:**
> /dev/sdb1 has gone 49710 days without being cheked, check forced.
Then the check pops right into 15, 21 og 18% before it stops, and then nothing more happens, it just stands there. I`ve tried many times.


Hello,

This is probably no help at all, but I just want to make sure you've left the computer at 18% for a good length of time?

I only say this because my partner keps rebooting her computer as the disk check kept stopping - but once we left it alone for 15 mins it was OK!

Perhaps another option for you is to boot with the live CD, and then at terminal you should be able to do this :

```
fsck /dev/sdb1
```

Not sure if you'll need sudo for that ...

Cheers
Callan

---

### Post by Fyksen on 2007-09-25
I had it on for a very long time, but nothing happend.

I have tried very many times, and finaly it didnt pop out from the startup screen, but the line went all over.

But after that, the screen went black, and nothing more happened. 

That happens every time now..

I`m going to try one more time, and see if I get any sort off error message.

---

