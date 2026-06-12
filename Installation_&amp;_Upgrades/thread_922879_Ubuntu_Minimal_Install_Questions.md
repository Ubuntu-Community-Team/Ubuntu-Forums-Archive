---
title: "Ubuntu Minimal Install Questions"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by BEND IT 7 on 2008-09-17
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)


Does this work for Ubuntu 8.04.1?

Does this require an internet connection (for packages and other installation procedures)?  

If so, how would I connect during installation?

How can I reconfigure hard drives during this install?

Will this be better than Puppy for an old 96 mb laptop with I think 3 gigs RAM if I configure it as minimal as possible?

---

### Post by oilchangeguy on 2008-09-17
"an old 96 mb laptop with I think 3 gigs RAM" you may want to try those specs again. and stick with puppy, or damn small linux.

---

### Post by Patb on 2008-09-17
> Does this work for Ubuntu 8.04.1?
Yes. There is no reason it shouldn't. 
> Does this require an internet connection (for packages and other installation procedures)?
Not essential. But the latest security updates will not be installed.  You also may have to edit your sources later either in Synaptic/Adept or manually.
> If so, how would I connect during installation?
If you have a network cable, try plugging it in before you start. If you have dial-up, forget it till after installation.
> How can I reconfigure hard drives during this install?
What do you mean by "reconfigure"?  If you mean partitioning, yes, there is a partitioning segment during install. I usually use the manual option so that I can see exactly what is going on. 
> Will this be better than Puppy for an old 96 mb laptop with I think 3 gigs RAM if I configure it as minimal as possible?
Can you be more specific.  96 Mb disk storage will not be big enough for anything other than DSL or Puppy.  If you mean 96 Mhz cpu speed, that is going to be slow - be patient. If you mean 96 Mb RAM (which is inconsistent with the 3 Gb you mention so I'm confused) that will be barely enough to run anything but Xubuntu at best.  Fluxbox (or Blackbox which I have never tried) would be the better choice because it is lighter than Xfce. 

Hope this helps. Cheers, Pat.

---

### Post by BEND IT 7 on 2008-09-17
Yes, woops.

I meant 96mb RAM and maybe a 3 gig hard drive.

The graphics engine is also probably the most old school I have ever seen.

---

### Post by Vivaldi Gloria on 2008-09-18
Read CLI in my sig. It needs at least 128MB ram.

---

### Post by cariboo on 2008-09-18
Acually if you don't need a gui, it will work quite well. I have a old emachine with a 400mhz cpu and 128MB ram, it works really well as an mp3 player. I use smbfs to connect a share from my server, and a program called randomplay in conjunction with mpg321 to play the tunes. I have ramdomplay set to not play repeats for 30 days. As you can see from the output of uptime:

```
uptime
 00:40:42 up 12 days,  7:33,  3 users,  load average: 0.20, 0.16, 0.10
```

I've got a ways to go before I start hearing the same music all over again.

Jim

---

### Post by snowpine on 2008-09-18
My advice is stick with Puppy. 

If your heart is set on something in the Ubuntu family, try Fluxbuntu 7.10. Nothing in the 8.04 family is going to work because of a bug in the installer with low memory systems; read here: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

---

