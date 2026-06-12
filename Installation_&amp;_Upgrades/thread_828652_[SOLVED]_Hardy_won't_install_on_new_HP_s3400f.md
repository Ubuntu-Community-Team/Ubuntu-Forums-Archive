---
title: "[SOLVED] Hardy won't install on new HP s3400f"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by bkline on 2008-06-13
I just picked up a new HP slimline desktop machine, partly selected because one of the reviewer on HP's site said he had successfully installed Linux on this model, albeit using CentOS, not Ubuntu (I'd rather stick with Ubuntu, as I have four other systems running Hardy).

With this system, I can't get past pushing the Enter key to start the install.  No matter what I do, the screen clears, the cursor blinks in the upper left corner, and that's it.

Here's what I've tried so far:

 * the standard i386 Hardy install CD
 * the alternate i386 Hardy install CD
 * verifying the integrity of the CDs (both of them)
 * memory tests
 * running the installed Windows Vista to ensure hardware OK
 * removing 'splash' from the boot line
 * removing 'quiet' from the boot line
 * adding 'nosplash' to the boot line
 * adding 'noapic' to the boot line
 * adding 'nolapic' to the boot line
 * adding 'acpi=off' to the boot line
 * adding 'pci=noacpi' to the boot line
 * adding 'break=bottom' to the boot line
 * adding 'break=top' to the boot line
 * all boot line modifications together (except 'break=top')

Here are the specs:
 * AMD Athlon 64 X2 dual-core 5200+ (2.70GHz)
 * Chipset NVIDIA nForce 430
 * 1MB L2 cache
 * bus speed 2000MT/s
 * 4GB PC2-6400 DDR2 SDRAM
 * 500GB 7200RPM SATA
 * nVidia GeForce 6150 SE graphics with turbo cache/ 128MB memory

I had much better luck earlier this year with an HP s3300t (different graphics: nVidia GeForce 7100/nForce 630i, rev a2), but they're not selling those any more.

Any tips for what else to try?  Any more specifics on the specs that would be useful?  Again, I'm sticking in the CD, booting up, selecting English, pressing F6 to edit the boot line, and pressing Enter to start the install, and that's as far as I get.  Don't think I've ever had a Linux installer of *any* distro give up this early in the process.  :(

---

### Post by bkline on 2008-06-17
> **bkline said:**
> With this system, I can't get past pushing the Enter key to start the install.  No matter what I do, the screen clears, the cursor blinks in the upper left corner, and that's it.

Here's what I've tried so far: ....

It was a lemon.  Took it back to the store, swapped it for another of the same model and started over again.  Smooth as silk.

---

### Post by PruneDog on 2008-07-02
I just bought the very same HP s3400f. I was wondering if you:

1. Installed 64-bit Ubuntu OS or the 32-Bit Version?
2. What type of monitor are you using?

I only ask because I loaded up the 64-Bit OS version and I have a 22" Acer widescreen monitor (AL2216W). Everything seems to be working fine...except my monitor is not displaying its native 1680 x 1050 resolution properly. I have it working on 1400 x 900. The problem is there is an annoying "Input Not Supported" graphic scrolling about the screen.

Do you have any ideas as to what may have happened? Thank you.

---

### Post by bkline on 2008-07-02
> **PruneDog said:**
> I just bought the very same HP s3400f. I was wondering if you:

1. Installed 64-bit Ubuntu OS or the 32-Bit Version?
2. What type of monitor are you using?

I'm running the 32-bit version with a 27.5" Hanspree monitor, using the native 1920x1200 resolution.  I had to fall back on NVIDIA drivers for another HP with the same footprint but slightly different specs (and video chip), but this just worked right out of the box.  I'd post my xorg.conf, but there's really nothing of interest in it (the vanilla "Configured Video Device/Configured Monitor").  I would hope it's not the 64-bit version that's causing your problem, but I don't really know.  Can't think of any other likely candidates.  Good luck.

---

### Post by PruneDog on 2008-07-03
Thank you for quick reply. I had a feeling that I had to be missing something simple. I consider myself a newbie, but a quick learner. I updated BIOS from HP's website. Easy enough. Then I just let the OS run all of its updates...all 215 of them!!! It took some time, but after a reboot all works well. No more screen resolution problems. As far as I can tell, everything seems to be working properly. I have not turned on any "eye candy" yet. I will keep you posted if I run into trouble seeing that we have the same exact computer system.

PS - Thanks for making my 22" monitor seem so small compared to your 27.5" whopper!

---

### Post by bkline on 2008-07-03
Glad things worked out.  As for the monitor size, my vision is probably much worse than yours.

---

### Post by PruneDog on 2008-07-03
Sorry to bug you again... I just bought the Slimline s3400f yesterday. Today was my first full day using it for business. I have not really taxed the processor/system besides running email and firefox for my work. It appears that some sort of fan (I can't tell if it is CPU or Power Supply) has been running all day. It does not throttle up and down; it just seems constant. The back of the machine is a little hot too. Is this normal?

I only ask because I used to have a laptop running all day as my setup for about the last 5 years. I am used to laptop fans running constantly - especially throttling up and down. So I am not sure if this is normal for the s3400f. Thanks for your help.

Happy 4th of July!

---

### Post by bkline on 2008-07-03
Neither of my HP Slimline boxes seems to run the fan at high speeds constantly, nor does either of them feel overly warm.  You might find it useful to install lm_sensors and see what temperatures it reports.

HHT,
Bob

---

### Post by alexzm1 on 2008-07-17
> **bkline said:**
> Neither of my HP Slimline boxes seems to run the fan at high speeds constantly, nor does either of them feel overly warm.  You might find it useful to install lm_sensors and see what temperatures it reports.

HHT,
Bob

any luck with the WLAN Drivers?

---

### Post by bkline on 2008-07-18
> **alexzm1 said:**
> any luck with the WLAN Drivers?

One of the machines didn't have the wireless option, but the other (the s3400f) did, and it worked perfectly.  I network that machine with a cable connection, but I tested the wireless to make sure it worked for the benefit of a colleague who was in the position of needing to replace a dying system and needed one which did wireless under Ubuntu.

HTH

---

