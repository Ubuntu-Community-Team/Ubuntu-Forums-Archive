---
title: "Graphical Corruption in Ubuntu Installer on an HD5450"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by LeaffyLeif on 2012-01-17
Okay, following my attempts with the server edition, I've resorted to the desktop edition. I've tried a number of things, including nomodeset and xforcevesa, to no avail. Without them, the screen is corrupted as soon as I hit "Install Ubuntu", and with them it crashes halfway through loading the installer, citing k10temp and SP5100 issues.

This is on an AMD Athlon II x2 7550 @ 2.5GHz with an XFX Radeon HD5450 Rage 512MB GDDR3 Silent - both of which are supposed to work.

Please, please, can someone help me.
Thanks,
Leif

---

### Post by LeaffyLeif on 2012-01-18
Attempted the following / Result:

**64-bit 11.10 Desktop Verbose**: SP5100_tco error, system halts.
**64-bit 11.10 Dekstop GUI**: Graphical corruption, pink and blue thick lines.
**32-bit 11.10 Desktop Verbose**: k10temp module fails, cites unreliability, system halts.
**32-bit 11.10 Desktop GUI**: Same as 64-bit.
**32-bit 11.04 Desktop Verbose**: SP5100_tco error, system halts.
**32-bit 11.04 Desktop GUI**: Graphical corruption, pink and blue think lines.

In the cases of **ALL GUI** trials, the drive is still going so I can assume it's still reading. All the above have been tried with "nomodeset=1" - this removes graphical corruption (where appropriate), but the Sp5100 and k10temp system halts still occur where noted.

I'd hate to think I can't run Ubuntu on here...

---

### Post by LeaffyLeif on 2012-01-18
Attempting the following this evening:

Removing HD5450, switching to integrated HD2100 on VGA.
Hypotheticall, this should allow me to get in to an 11.10 install environment as the SP5100 issue is linked to the HD5450. 

Will post results this evening.

---

### Post by coffeecat on 2012-01-18
> **LeaffyLeif said:**
> Removing HD5450, switching to integrated HD2100 on VGA.
Hypotheticall, this should allow me to get in to an 11.10 install environment as the SP5100 issue is linked to the HD5450. 

Good luck with that. I've not much of substance to offer but I can say that my Asus ATI Radeon HD5450 works just fine. I'm posting from a machine using it just now - 64-bit 11.10 using the default open source driver.

Have you tried your HD5450 card on another machine and/or with another OS? The HD5450 GPU should not be a problem in itself. Perhaps you need to exclude a hardware fault.

---

### Post by LeaffyLeif on 2012-01-18
The original OS was Windows Server 08 R2, on which it worked fine. The SP5100 is related to a component of the SouthBridge that communicates with the GPU, and the k10temp is just a thermal sensor. My figuring is that trying it without the HD5450 makes it a driver issue as opposed to a hardware issue. 

HD2100's are known to work.

---

### Post by LeaffyLeif on 2012-01-18
After removing the HD5450 and plugging a VGA cable into the onboard X1250, it will successfully display the "splash". HOWEVER, the splash displays for about 60-90 seconds, and then just leaves me with a perpetual purple screen. Nothing happens. CD drive stops going (and refuses to open, too). 

Now I'm just sad :(

[Edit] running in verbose, see what happens

[Edit 2] Runs for 122 seconds before displaying graphical corruption. Manages to get past the SP5100 and k10temp issue, but then says SOMETHING and dies. After that the hardware is unresponsive, so I'm assuming a kernel panic... Any ideas?

---

### Post by alphacrucis2 on 2012-01-18
Which version of Ubuntu are you trying to install? 11.10?

---

### Post by LeaffyLeif on 2012-01-18
11.10 64-bit Desktop

[Edit] Fedora ALSO does a similar thing - displays the verbose and then dies.

---

### Post by darkod on 2012-01-18
If you are using a CD areyou burning it on low speeds, not more than 8x or 10x?

CDs these days go up to 56x and many people leave burning at default but for OS install cd you shouldn't really go over 8x.

It sounds ridiculous but a lot of issues have been known to come from a fast burned cd and/or ISO file corrupted during download.

---

### Post by LeaffyLeif on 2012-01-18
CDs burnt at 2x, 4x and 8x, same result with all of them D:

[Edit] Interestingly, removing my secondary hard disk gets me 5 extra seconds of boot time, but it still fails in the same way...

---

### Post by darkod on 2012-01-18
> **LeaffyLeif said:**
> CDs burnt at 2x, 4x and 8x, same result with all of them D:

That rules it out then.
Sorry, can't help much with the issues you are seeing. :(

---

### Post by LeaffyLeif on 2012-01-18
Right, I'm typing this from the same CD I've attempted to use - running as a LiveCD on an i7-740QM @ 1.73GHz (quad), 8GB DDR3 1333MHz, GTX460m 1.5GB GDDR5.

It's definitely the server. So far I've removed the HD5450, solved one problem, and disconnected my storage drive (leaving the system drive there) which granted me 5 more seconds of boot time before dying still.

---

### Post by LeaffyLeif on 2012-01-18
PROGRESS!

Using a 10.04 LTS disk I have been able to boot all the way through to the live cd "splash". This stays on for 30 seconds before the screen just goes black - it's on, but it's not outputting. Same for verbose - it gets to "Setting sensor limits" and then the screen clears to black.

BUT: With 10.04, everything is still responsive - it hasn't died, it's just stopped displaying...

This is an ATI X1250 integrated. PLEASE PEOPLE!!

---

