---
title: "ATI Radeon 5850 and Ubuntu 10.04 don't work together"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by xbaez on 2010-05-24
Hello. I was a happy Ubuntu 9.10 user, ATI Radeon worked great.

I did a do-dist-upgrade (or whatever the command is), and I was unable to run my desktop

I downloaded the CD, burned it, and installed it from scratch

I have nForce 730i with included GeForce 9300 graphic cards.
When I go to the BIOS and change the onboard video to ALWAYS ENABLE, I am able to use Ubuntu

However, when I go to the BIOS, and select onboard video enabled only when no PCI express card is available, then all I see is a purple screen

So, the main issue is this
1) When I run Ubuntu 10.04 from my onboard video card, it works great
2) When I run Ubuntu 10.04 from my ATI Radeon 5850, all I see is a purple screen
3) These problems never existed in Ubuntu 9.10


Thanks in advance

---

### Post by quadproc on 2010-05-24
> **xbaez said:**
> Hello. I was a happy Ubuntu 9.10 user, ATI Radeon worked great.
...
However, when I go to the BIOS, and select onboard video enabled only when no PCI express card is available, then all I see is a purple screen

You might be having trouble with kernel mode setting (KMS).  This feature was previously turned off in earlier releases but in 10.4 it now defaults to on.  You may need to specify nomodeset in your grub entry for the 10.4 version.

quadproc

---

### Post by xbaez on 2010-05-24
> **quadproc said:**
> You might be having trouble with kernel mode setting (KMS).  This feature was previously turned off in earlier releases but in 10.4 it now defaults to on.  You may need to specify nomodeset in your grub entry for the 10.4 version.

quadproc


Thanks for your help
would you mind helping me please with that?

Grub 2 is super confusing for me

how do I turn off nomodeset?

---

### Post by jmarz on 2010-05-27
thanks to those that posted about it - I finally got my set up fixed so I don't have to mess with the low graphics notice

 but hope this helps

one member posted this-
[1) Hold down Shift while booting to get to grub.
2) Press 'e'. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.
]]

I just let it go to grub and then hit the e key

use the dn arrow to get to the line that has the quiet splash
use arrow key to get to the words quiet splash and delete them and type in nomodeset
then do #3

after the reboot I still did have the low graph notice.

I was having nvidia issues LOL- maybe change the name and try the same fix?


so i went to synaptic and removed all nvidia drivers -
used the search there to find it fast
did a reboot and still had the notice.

went back into synap and reloaded all nvidia stuff- clicked to sort by newest

and reinstalled a lot of the nv stuff from the top of that list - unless the description made me think it wasn't what i needed

did a reboot then - and finally it all worked and no stupid notice.


good luck I hope it works for you- I've been messing with trying to fix mine on & off for a month or so

Dual boot Ub 10+ with XP

---

### Post by xbaez on 2010-05-27
I appreciate your reply, will try this and I'll let you know what happened

---

