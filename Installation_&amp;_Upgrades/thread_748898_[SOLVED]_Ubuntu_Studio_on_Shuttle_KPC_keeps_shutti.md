---
title: "[SOLVED] Ubuntu Studio on Shuttle KPC keeps shutting down on boot"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by gfixler on 2008-04-07
I just got a Shuttle KPC, and after some hell trying to install Ubuntu Studio from USB thumbdrive, and external CD drive (had to finally crack the case, and run ide/power cables to an external internal optical drive for the alternate install disc), I've got it installed.

I was able to boot up from the HDD, and installed the 150 or so updates that it notified me about. Now it crashes when it tries to load X, giving me a blue screen with X crash text, but then it kicks back to a shell, and a few seconds later, shuts down the PC. If I run recovery mode, it makes it pretty far, and then about the time it would probably be giving me a prompt, it shuts down!

Any ideas what I can do here?

---

### Post by ad_267 on 2008-04-08
You could try reconfiguring X with "sudo dpkg-reconfigure -phigh xserver-xorg"

---

### Post by gfixler on 2008-04-08
> **ad_267 said:**
> You could try reconfiguring X with "sudo dpkg-reconfigure -phigh xserver-xorg"

Thanks for the info. I'm storing it away in my brain for now, because I got it working. Rather, it just works again. I have no idea why, but leaving it off for a bit, and turning it back on, it went right to the graphical login.

It could have something to do with heat. It kept shutting itself down during boots yesterday, claiming in the startup messages that it had hit some critical temperature, and was going to thermal shutoff (78°-79°F). Maybe not, but anyway, at least it's working fine now. Thanks!

---

### Post by Partyboi2 on 2008-04-08
If you are having heating problems, check that the power supply fan and cpu fan is working and that there is not a build up of dust.

---

### Post by gfixler on 2008-04-08
> **Partyboi2 said:**
> If you are having heating problems, check that the power supply fan and cpu fan is working and that there is not a build up of dust.

I just unboxed it brand new 2 days ago, so definitely no dust, and with all the hookings up of cables in the last few days while it's been on, I've definitely felt it venting hot air out the back. I've been talking to someone who mentioned I have the stock Intel chip cooler, though, which is pretty simple. I might cannibalize an old, dead Shuttle for its ICE 3 heat pipe. That should cool it down a lot. I don't think I'm having any actual heat problems, despite the air being pretty warm coming out of it, but I'm not really sure yet.

Thanks for the suggestions.

---

### Post by Rhubarb on 2008-04-08
This sound similar to my shuttle SD32G2 box I'm using now.
For me there's a problem in the shuttle's BIOS that makes it problematic to run the linux kernel with ACPI enabled.
So, when grub comes up, try changing your boot line to include "acpi=off".

If you want me to be more specific, let me know.

I have read online a solution to this: compile your own linux kernel, there are some minor ACPI related options that you should change to fix this.

---

### Post by gfixler on 2008-04-09
Interesting. I don't know if I'm quite ready to compile my whole own kernel yet, but it's good info. Thanks, Rhubarb!

---

