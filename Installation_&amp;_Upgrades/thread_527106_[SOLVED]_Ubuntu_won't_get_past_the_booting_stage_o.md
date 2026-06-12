---
title: "[SOLVED] Ubuntu won't get past the booting stage on self built PC"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by okey666 on 2007-08-16
I have self built a pc for the sole purpose of running Linux on it. None of my distros will boot. Ubuntu goes to the menu stage where it asks you what you want to do ie. boot it, boot it in safe mode etc. Then when I select boot and install the splash screen appears and the orange bar moves. After doing this for a few minutes it comes up with a list of errors which increases by one every minute or so. I think it could be the SATA DVD/Cd drive because Mandriva says it can not find the drive.
Please could anybody help me find the problem and fix it, because having a good PC that does nothing is getting frustrating!

---

### Post by heimo on 2007-08-16
> **okey666 said:**
> After doing this for a few minutes it comes up with a list of errors which increases by one every minute or so. 

It'll be lot easier for people to help you if you give as much information as possible. Especially the exact error messages.

---

### Post by okey666 on 2007-08-16
Sorry, I am new to this, the errors are:
[136.538569] ata4.00: failed to set xfermode (err_nask=0x4)
[141.042051] buffer I/O error on device fd0, logical block 0

these errors then rpeat themselves endlessly (I have not seen them stop yet) down the screen, with a waiting time of about 1 minute between them, the only difference between them it the number in the square brackets.






Like I said I am running a home built system with:
Abit AB9 Quadro GT motherboard
Intel E6600 Core 2 Duo on a LGA775 slot processor
Palit nVidia 8600 GT graphics card
2GB DDR2 dual channel ram
250 Hitachi SATAII  hard drive
CD/DVD +/- RW SATA drive

it also has an Award Bios

---

### Post by okey666 on 2007-08-16
After waiting for about 45mins the folowing message came up on the screen:
/bin/sh: can't access tty; job control turned off (initramfs)

Then the screen went black.

---

### Post by Arthur Archnix on 2007-08-16
1 In your BIOS, check to set sata to compatibility mode. Any difference?

2. Check your cables. 

3. Rinse and repeat.

4. If that doesn't work, try unplugging the hard-drive completely and booting the lived cd, does it work?

---

### Post by okey666 on 2007-08-16
> **Arthur Archnix said:**
> 1 In your BIOS, check to set sata to compatibility mode. Any difference?

2. Check your cables. 

3. Rinse and repeat.

4. If that doesn't work, try unplugging the hard-drive completely and booting the lived cd, does it work?
Ok will do

---

### Post by okey666 on 2007-08-16
Fixed it!

I did what you said unplugged the hard drive and ran it totally live cd. When that worked I replugged the hard drive on SATA 2 and it worked!!!!

It is installing now!

Thanks everyone.

---

### Post by Ryba on 2007-08-16
> **okey666 said:**
> After doing this for a few minutes it comes up with a list of errors which increases by one every minute or so. I think it could be the SATA DVD/Cd drive because Mandriva says it can not find the drive.

I haven't read what anyone elses response to this is so if they answered ignore this post. I have had a bad dvd drive before in linux and it has spit out tons and error messages every few seconds but *that* never prevented anything in linux from working (unless it was using the dvd).

The problem sounds like it might be related to something else. I didn't see enough detail in the problem but most likely there is another error buried in that slew of errors that is causing the problem.

If your ubuntu boot disk (that you used to install the system) was able to boot, there is nothing wrong on a hardware level actually.

Which version of ubuntu did you try (gutsy has quite a few boot problems with it I find but then again it isn't suppose to be stable yet either).

---

### Post by Arthur Archnix on 2007-08-16
> **okey666 said:**
> Fixed it!

I did what you said unplugged the hard drive and ran it totally live cd. When that worked I replugged the hard drive on SATA 2 and it worked!!!!

It is installing now!

Thanks everyone.

Great. Use thread tools to close the thread as solved. Best,

---

