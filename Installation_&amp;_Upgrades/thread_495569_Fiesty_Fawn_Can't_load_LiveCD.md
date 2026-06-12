---
title: "Fiesty Fawn: Can't load LiveCD"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by The-Sam on 2007-07-08
When using the Ubuntu 7.04 AMD64 Live CD (on an AMD Athlon 64 3800+), just after I select "Start or install Ubuntu" and "Loading Linux Kernel" appears, the screen goes blank, and the num lock and scroll lock lights on my keyboard start flashing. Can anyone help me?

---

### Post by koshari on 2007-07-08
have you tried the option noaspi? sometimes this will help, 

Hit F6 on the boot menu, delete "quiet splash"  and try booting, note the last line before it barfs.

for more reference

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by bigken on 2007-07-08
how did you burn the cd 

what graphics card do you have 

how much ram do you have 

have tried to burn another cd if you havent burn a new one as slow as possible

---

### Post by The-Sam on 2007-07-08
> **koshari said:**
> have you tried the option noaspi? sometimes this will help, 

Hit F6 on the boot menu, delete "quiet splash"  and try booting, note the last line before it barfs.

for more reference

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I'll try that now (your post changed since I started replying!).

> **bigken said:**
> how did you burn the cd 

what graphics card do you have 

how much ram do you have 

have tried to burn another cd if you havent burn a new one as slow as possible

I used InfraRecorder on all the standard settings (i.e. top speed, etc) to burn the ISO onto a DVD (no spare CDs!).

My graphics card is an ATI Radeon X800, and I have 512 MB of RAM.

I'll try to burn another disk once I've tried without aspi.

I forgot to say in my first post that I've used an Ubuntu Live CD before with no problem, but I didn't install it at that time (I think it was 6.06). My hardware hasn't changed since.

---

### Post by The-Sam on 2007-07-08
(Sorry for double post)

Using noaspi has no effect. 

When I removed quiet splash, after a load of stuff that went too quickly to catch, it alternated quite slowly between these two lines:

end_request: I/O error dev fd0, sector 0
buffer I/O error on device fd0, logical block 0

Before stopping (I pressed the reset button after about a minute) on:

squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher

---

### Post by bigken on 2007-07-08
looks like its trying to boot from your floppy ?

---

### Post by The-Sam on 2007-07-08
> **bigken said:**
> looks like its trying to boot from your floppy ?

I don't have a floppy drive!

---

### Post by bigken on 2007-07-08
take a look [here ]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306")

---

### Post by The-Sam on 2007-07-08
> **bigken said:**
> take a look [here ]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306")

Thanks!

After leaving it for another 5-10 minutes, it carried on normally with no problems - I'm using the Live CD to post this. :)

---

### Post by bigken on 2007-07-08
great hope all goes ok for you \\:D/

---

