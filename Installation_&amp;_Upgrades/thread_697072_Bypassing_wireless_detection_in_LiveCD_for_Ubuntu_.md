---
title: "Bypassing wireless detection in LiveCD for Ubuntu 7.10"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by arafalov on 2008-02-14
I am trying to boot LiveCD Ubuntu latest (7.10?) and have a problem with broadcom wireless card. I found the solutions on how to extract the firmware, etc but they all talk about modifying already installed OS. I cannot even get to the welcome screen. Installing Ubuntu (at this point) is not an option.

Is there any way to bypass wireless detection during the boot, perhaps with one of the boot flag options? I could not find a document listing all the possible boot flags, so could not figure it out myself.

I am trying to boot without wired network connected, so I am effectively trying to bypass all network,  I am not sure if that makes the solution easier or harder.

Thank you,
    Alex.

---

### Post by Pumalite on 2008-02-14
The easiest way is to get wired to the Internet with DHCP.

---

### Post by arafalov on 2008-02-15
Thanks Pumalite,

Does it mean that if I am connecting to the router with wired line, the boot process will ignore the wireless? 

So, Ubuntu needs to access the internet to boot up? That's strange.

---

### Post by Pumalite on 2008-02-15
It's nor strange. That's how it builds your repositories among other things.

---

### Post by lswest on 2008-02-15
hmm, i've never actually needed that for any of the liveCDs i've used (i have a broadcom card too, which i set up with ndiswrapper after the fact, and set up the repositories by uncommenting the lines which were commented) Also, no wired connection at the time.  Well, try it and see if it works, I'll have a look around and see if a boot parameter disables networking.

---

### Post by Pumalite on 2008-02-15
Here is a guide and a collection of boot parameters to try, if you feel like it:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

---

### Post by arafalov on 2008-02-17
Didn't work even with a LAN.  It still gets to the 'microcode ... not available' message and just displays that repeatedly.

I have also tried netcfg/disable_dhcp as an option to add to 'quiet' and the rest, but it did not seem to make any difference. I tried removing 'quiet' option and that did nothing I could see.

Is there anything else I could try? I would like to try the latest Ubuntu, but wiping out Vista without knowing the hardware would work is too large a step.

---

