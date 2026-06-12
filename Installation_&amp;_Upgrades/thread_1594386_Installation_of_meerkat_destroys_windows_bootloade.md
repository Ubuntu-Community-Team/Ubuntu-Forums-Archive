---
title: "Installation of meerkat destroys windows bootloader"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by lordtillt on 2010-10-12
Hi there,

I'm experiencing massive problems after I upgraded to 10.10 from 10.04.

I assume the upgrading process overrid my Windows Bootloader, which I desperately need.
I'm using a business laptop, so I don't have any access to the BIOS (if I'd had, I would just get a live-cd a get the **** repaired) and I can't modify the first partition (C:).

The more I write here, the more I realise it's my own fault, because I chose the location for GRUB2 on sda1, which is Windows...
Anyway - I just get, after starting, a GRUB-error message, which tells me, it couldn't find the device (a 10mile long uuid). I assume it's because I installed Ubuntu on a virtual harddisk (I'm not sure if that's the correct description, I'm not sure, but I think the results are *.rom files) using the Windows Ubuntu Installer. Which in my opinion means: UUID's pretty messed up.

That means, I installed Ubuntu on the Z: partition of windows without deleting any data from it but creating multiple *.rom (still not sure if that was the ending) files.

I now have simply a grub rescue> prompt, but I can't even type 'help' in there...

I would be VERY grateful if somebody could help me - I'm not sure if installing Ubuntu in my company is exactly legal, so I don't want to contact them to set up everything again...

Regards,
Till

---

### Post by Rubi1200 on 2010-10-12
If you mean you installed Ubuntu using Wubi then there is a fix to get Windows back. However, you will need either the Windows installation/recovery CD or an Ubuntu CD.

We also need to know which version of Windows you have installed.

EDIT: oops, just reread and realized you cannot access BIOS; why not, is it password protected?

---

### Post by lordtillt on 2010-10-12
I can't boot from CD due to BIOS restriction :(

I use XPPro.

Is there any way to get a CD running from that grub recovery shell?

---

### Post by Rubi1200 on 2010-10-12
> **lordtillt said:**
> I can't boot from CD due to BIOS restriction :(

I use XPPro.

Is there any way to get a CD running from that grub recovery shell?
Not as far as I know; the best you might hope to achieve (also doubtful because of the scenario) is to get back into Ubuntu. But that does not solve your problem.

I hope someone else comes along and offers another solution. Otherwise you may have little choice but to come clean at work, tell them what has happened, and tell them that the solution is to restore the Windows bootloader.

Here is the link for how to do this if it becomes necessary:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by lordtillt on 2010-10-12
Mhm, damn - but thank you for your help. I think itll be the best to hope IT support will understand my enthusiasm for ubuntu ;)

---

