---
title: "Problem with runing live CD, seek advice before I install"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by rrig004 on 2007-01-06
I Have used ubuntu at uni and now want to install it on my new laptop. I tryed to run the live CD to test things out, while it was loading everything was going ok untill the following message was printed out and it stalled and I had to restart the computer.

   firmware_helper[4807]:main error loading '/lib/firmware/bcm43xx_microcode5.fw'
   for device 'class/firmware/0000:03:00.' with driver 'bcm43xx
   [17179668.244000] bcm43xx: error: microcode “bcm43xx_microcode5.fw” not available
   or load failed.
   [17179668.324000] bcm43xx: error: microcode “bcm43xx_microcode5.fw” not available
   or load failed.
   firmware_helper[4819]:main error loading '/lib/firmware/bcm43xx_microcode5.fw'
   for device 'class/firmware/0000:03:00.' with driver 'bcm43xx

   * starting PCMCIA services...								       [OK]
   * PCMCIA not present
   * Loading manual drivers...									        [OK]
   mount: Function not implemented.

After that I changed the video setting at the boot screen from VGA to one of the other settings and the same messages flashed passed, but this time it loaded into ubuntu no problem.

So what I would like to know is that given this problem are there are any problems I could expect when I install, is there anything that I should be prepared for?

I would appreciate any help that anyone may offer.

---

### Post by bmt on 2007-01-08
I am not an expert ;-), but I would say that there is nothing to worry about.

The lines with [OK] at the end have all executed correctly, so they're nothing to be concerned about.  '* PCMCIA not present' suggests to me that there is no PCCard in the machine -- the drivers have loaded correctly ([OK] on the line above), but there is nothing further to be done at that time.  When you plug a card in, they will be ready.

The 'mount: Function not implemented.' seems to be quite common when running a LiveCD.  Apparently, it's a timing issue or a security thing with a LiveCD, depending on where you read it!  I didn't look too far, but no-one I read reported any difficulties on an installed system.  Google 'mount: Function not implemented' if you want to check for yourself.

---

