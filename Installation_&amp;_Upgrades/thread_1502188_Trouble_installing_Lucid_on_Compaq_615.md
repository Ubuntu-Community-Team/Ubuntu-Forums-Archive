---
title: "Trouble installing Lucid on Compaq 615"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by bigseb on 2010-06-05
My wife has a Compaq 615 on which she wants me to install Lucid 32 bit. I have the install disk but it doesn't seem to want to install. What happens when I boot up from disk is it show the purple screen, asks me which language I want and then shows the list of options. If I choose 'try Ubuntu without installing' the screen goes black with a cursor blinking in the top left for a few seconds. About a minute later the disk drive stops spinning and nothing, it just hangs there. If I choose 'Install Ubuntu' then the same thing happens except this time the disk drive just keeps spinning (still without anything happening). With the other options I get the same result as if I had chosen 'Try Ubuntu without installing'. Her laptop does meet the minimum requirements (she has: AMD X2 2.1 GHz, ATI Radeon HD3200, 2Gb RAM, 160Gb hard disk.

I tried my x64 disks on her laptop and get the same result!! All these disks by the way work perfectly on my PC (and two friends who tried them out too) so I'm stumped. Why, oh why is it not installing Ubuntu 10.04 x86?

Please help!

---

### Post by bigseb on 2010-06-05
Just discovered something interesting: my Karmic disks work 100%! This must be specific to Lucid then. Any ideas on how to fix as I'd much rather install Lucid than Karmic on her machine...

---

### Post by bigseb on 2010-06-06
Bump

---

### Post by davidmohammed on 2010-06-06
When pressing F6 edit the boot string so that it reads

**nomodeset** quiet splash --

if that doesnt work try

**nomodeset xforcevesa** quiet splash --

---

### Post by bigseb on 2010-06-07
> **davidmohammed said:**
> When pressing F6 edit the boot string so that it reads

**nomodeset** quiet splash --

if that doesnt work try

**nomodeset xforcevesa** quiet splash --

tried that... The first one doesn't work, the second option isn't there. Help!

---

### Post by davidmohammed on 2010-06-07
hi there,
  you'll notice at the bottom the actual boot string used.  Edit that line.  Don't use the "check box" options that have noapic, nomodeset etc.

---

### Post by bigseb on 2010-06-07
Ok wait, I see now what you mean, I must type it in. Well I did that and still nothing. It just hangs :( Strangely, I tried the x64 disks and they work perfectly!?!

---

### Post by darkod on 2010-06-07
How about F6 and using Safe Graphics?

---

### Post by bigseb on 2010-06-08
> **darkod said:**
> How about F6 and using Safe Graphics?

Thanks. I'll try this as soon as I get a chance, prolly only tonight.

---

### Post by bigseb on 2010-06-08
> **darkod said:**
> How about F6 and using Safe Graphics?

Just checked... where is safe graphics mode?? Or to be more precise which option is it? None of those listed are called safe graphics...

---

### Post by thor187 on 2010-07-05
I also have the same issue on boot up, I can not get to the start screen. I have the problem with Karmic, but when I loaded Kubuntu 9.10 it works no problem, but much prefer Ubuntu. I tried mounting the grub and editing that from Live CD, how do you go into safe graphics from the boot up???

---

### Post by a.kyppo on 2010-07-15
I just bought Compaq 615. I was confused why it did'nt boot Ubuntu from live-cd. Then I added **nolapic** as a boot parameter in ubuntu boot setup and it worked. After installation I rebooted and it did'nt boot from hd. I added **nolapic** and** nodmraid** as boot parameters. Then I opened **/usr/share/grub/default/grub**(as superuser of course) and edited line 10 to look like this: **GRUB_CMDLINE_LINUX="nolapic nodmraid"**
Then I saved it. After it I ran **update-grub** in terminal and rebooted and it worked.

---

### Post by bigseb on 2010-07-15
> **a.kyppo said:**
> I just bought Compaq 615. I was confused why it did'nt boot Ubuntu from live-cd. Then I added **nolapic** as a boot parameter in ubuntu boot setup and it worked. After installation I rebooted and it did'nt boot from hd. I added **nolapic** and** nodmraid** as boot parameters. Then I opened **/usr/share/grub/default/grub**(as superuser of course) and edited line 10 to look like this: **GRUB_CMDLINE_LINUX="nolapic nodmraid"**
Then I saved it. After it I ran **update-grub** in terminal and rebooted and it worked.


Interesting. I solved the problem by installing 10.04 x64. That works like a charm, Weird, huh?

---

