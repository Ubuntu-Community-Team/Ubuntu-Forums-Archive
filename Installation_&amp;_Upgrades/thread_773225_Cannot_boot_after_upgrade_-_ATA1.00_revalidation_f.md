---
title: "Cannot boot after upgrade - ATA1.00: revalidation failed"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by banjobacon on 2008-04-28
I upgraded from Gutsy to Hardy via update-manager. The upgrade seemed to go well, until I rebooted the computer. If I let the computer boot to the default kernel, 2.6.24-16, I get the following error:

> ATA1.00: revalidation failed (errno=-5)

Then the same lines are repeated over and over, saying things like "ATA2.00 Exemption Emask" and "status: {DRDY}". This repeats indefinitely until I hold down the power button and the computer turns off. 

I can only boot into Ubuntu if I select a different kernel in GRUB (2.6.24-14, though my graphics driver doesn't seem to work with this kernel), or if I boot 2.6.24-16 in recovery mode. When booting in recovery mode, Ubuntu seems to boot up without any issues. I select "Resume" when prompted, and can use my computer normally. 

Any help?

---

### Post by Gordone on 2008-04-29
Hi,

I'm having exactly the same problem. Although recovery mode gives me the same problem. 
Does changing the boot parameters help at all (adding noapic,nolapic,etc in the grub)?


What are your specs?
Mine are:

1.8 Ghz AMD Semperon
1GB DDR2
256MB ATI Radeon 9550
40 GB IDE Drive
40x LG Lightscribe DVD-Writer

---

### Post by RogerTX on 2008-04-29
> **Gordone said:**
> Hi,

I'm having exactly the same problem. Although recovery mode gives me the same problem. 
Does changing the boot parameters help at all (adding noapic,nolapic,etc in the grub)?


What are your specs?
Mine are:

1.8 Ghz AMD Semperon
1GB DDR2
256MB ATI Radeon 9550
40 GB IDE Drive
40x LG Lightscribe DVD-Writer

I'm having the same problem.  I haven't tried to change the boot parameters -- where do I find what they mean?  I was running GG with no troubles.

I have a 250G SATA drive.  It's a Dell computer, purchased around Christmas last year.

---

### Post by banjobacon on 2008-04-30
Well, it turns out I can sometimes boot normally, and booting in recovery mode fails, too. No noticeable pattern; it seems to be random.

> **RogerTX said:**
> I have a 250G SATA drive.  It's a Dell computer, purchased around Christmas last year.

I, too, have a Dell. N-series desktop with Ubuntu preinstalled, purchased a few months ago

---

### Post by tarrmd on 2008-05-01
I'm having the same problem as well....

Upgraded from Gutsy to Hardy...

At boot, I get

ata1.00: revalidation failed (errno=-5)

a couple times, then the computer reboots.

After several of these auto-reboots it will boot successfully.

This is on a Dell Inspiron 530s

---

### Post by tarrmd on 2008-05-01
Ok - I found a fix for this in this thread:

[http://ubuntuforums.org/showthread.php?t=767668](http://ubuntuforums.org/showthread.php?t=767668)

---

### Post by beerzoids on 2008-05-01
I'm getting the same thing.
 
**ATA2.00 Exception Emask 0x0 SACT 0x0 SERR 0x0 ACTION 0x2 FROZEN CMD A0/00300:00:24:00/00:00:00:00:00/a0. TAG 0 PIO36 IN STATUS:{DRDY}**
 
over and over and over and over again.
 
Dell Inspiron S30 Duo processor E4400 (2.00ghz) 
2GB DDR2 SDRAM at 667mhz
320GB ATA 2 Hard Drive
  
Edit: Fix in prior post does not work for me. Just gives me new error.

Edit 2: Fix did work. After changing the kernel, second line, must hit enter, not escape

---

### Post by Gordone on 2008-05-04
Hi,

ja, that didn't fix my problem (its seems like everyone else with the problem had newish Dells). I suspect my issue is to do with my harddrive being really old (6 years or so). I'm researching all the other error messages I get.

Cheers

---

### Post by banjobacon on 2008-05-06
I edited the file menu.lst to include "noapic apic=off", but this didn't help at all. I couldn't even boot successfully once.

---

### Post by Em-Buntu on 2008-05-06
> **banjobacon said:**
> I upgraded from Gutsy to Hardy via update-manager. The upgrade seemed to go well, until I rebooted the computer. If I let the computer boot to the default kernel, 2.6.24-16, I get the following error:



Then the same lines are repeated over and over, saying things like "ATA2.00 Exemption Emask" and "status: {DRDY}". This repeats indefinitely until I hold down the power button and the computer turns off. 

I can only boot into Ubuntu if I select a different kernel in GRUB (2.6.24-14, though my graphics driver doesn't seem to work with this kernel), or if I boot 2.6.24-16 in recovery mode. When booting in recovery mode, Ubuntu seems to boot up without any issues. I select "Resume" when prompted, and can use my computer normally. 

Any help?

Whie installing on a 20GB ATA100 drive, I received the same error. It just kep repeating itself over and over until it just crashed.

Someone else on the board posted to install Hardy, wait until you get to the install screen than hit <F6>. This will put you into the cMD prompt where you should enter;
all_generic_ide floppy=off irqpoll

After doing this, the system completed the install, however it ran very poorly to the point of being unusable.

I ended up replacing the ATA100 drive with a newer ATA133.
I still had to do the cmd disabling irqpolling, but after the install everything ran well and according to expectations.

I put the removed ATA100 drive into another system, loaded Win2000, and it runs like a top. So, the drive isn't bad. Go figure.

Good luck

---

### Post by RogerTX on 2008-06-10
> **banjobacon said:**
> I edited the file menu.lst to include "noapic apic=off", but this didn't help at all. I couldn't even boot successfully once.

Well, my experience with "apic=off noapic" just gave me a new set of I/O errors and threw me into Busybox, I think it's called.

However, when I used "irqpoll", everything booted up just fine!  So, I'll be adding that to grub to make it permanent.

---

