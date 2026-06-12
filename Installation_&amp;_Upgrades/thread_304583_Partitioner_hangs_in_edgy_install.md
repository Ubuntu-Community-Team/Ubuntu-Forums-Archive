---
title: "Partitioner hangs in edgy install"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by cisbrane on 2006-11-22
Hey,

I am trying to install Edgy on a Dell Dimension 8200 Intel Pentium 4 1.8GHz 256MB RAM

So I get to the step about partitioning and i want to manually partition. a gparted window appears, and after a min or two my computer completely freezes. I've tried the normal mode and the "safe graphics mode" and neither of them seemed to make any difference....

any suggestions on what i should do to get around this?

Also, when trying to set my time zone, if i click on set time and go back to the install window, the install program freezes but the rest of the computer is ok...

thanks

--cisbrane

---

### Post by ingo on 2006-11-22
hm... have you tried the alternative CD? It is exactly the same but does not include a graphical installer. It might help you get round your particular problem.

---

### Post by cisbrane on 2006-11-22
I'll give it a shot. thanks

---

### Post by cisbrane on 2006-11-23
yup that did it. thanks

---

### Post by the_joker on 2006-11-23
> **ingo said:**
> hm... have you tried the alternative CD? It is exactly the same but does not include a graphical installer. It might help you get round your particular problem.
Does anyone have any idea why this is happening? I'm having the same problem as the OP, where the partitioner hangs when attempting to set partitions manually.

I did not have this problem when installing Dapper.

While I'm happy to download the alternate CD, I think that just suggesting it as a panacea is probably not a good idea. Not everyone is on broadband yet, and many people have shaping limits on their accounts, making it difficult to justify downloading two CD images.

If anyone knows *why* the partitioning tool fails, I'd really like to know about it.

Ah well, now to use the alternate CD. ;)

---

### Post by xeo_Nightwing on 2006-11-23
I have an Acer Aspire 3613LCi laptop with a very similar element. I sucsessfully installed the Edgy Eft Live cd on my Athlon XP 3200+ 64-bit machine, running really good actually I must say, having used amlmost every major distro out there, I quite enjoy this version of Ubuntu, runner up, Open Suse 10.1, after that, not crazy about any other distro out there really atm. 

My laptop seems to be having a bit of a more unique problem with the Live cd though, it's not freezing solid at GPart, instead, it's freezing trying to start the installer altogether. I've tried both starting the installer via the desktop icon and the System->Administration menu, no difference. It just lags out like there's no tomorrow and yesterday and today sucked harsh. etc. I've tried specifying "noapic" and "nolapic" to grub, no difference. When I try for the installer, I don't even see so much as a task saying that it's attempting to start and Administration program. GPartEd can at least do that much but even it will eventually freeze once it starts to draw a vid-window. Have tried restarting X when it freezes, tried changing TTY's, tried CTRL-ALT-DEL to get the system to start shutting down...Nothing, she's locked up good and needs a one finger solute.

Don't really feel like downloading the alternative ISO and re-burning, so I just installed one of the Breezy Badger and apt-get dist-upgrade'd it to Dapper, posting this, then going for Edgy. Very annoying problem for a magor release. Only other info worth mentioning is that right before GDM starts appearing, it complains about my 802.11b/g NIC's firmware for who know's what reason. BCM4318 is it's model #.

Anyone else encountered freezing else where besides just running GPartEd durring the Installer?  Firefox runs good from what I can recall too. Yesterday that I tried it last so my memory is dead already if Firefox did run smoothly or not but I think it did.

--xeo_Nightwing
<deadmatrix@gmail.com>

---

