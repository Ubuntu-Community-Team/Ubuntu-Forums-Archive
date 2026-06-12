---
title: "mounting none on /dev failed No such device"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mikio on 2010-03-22
hi,

i get this message during booting:

mount: mounting none on /dev failed No such device

that is - after the grub2 screen. before the plymouth screen - which shows up for only a moment before gdm kicks in. ie - i have this message for most of the boot processes.

it does not seem to affect the system after everything is loaded.

thanks

---

### Post by VMC on 2010-03-22
> **mikio said:**
> hi,

i get this message during booting:

mount: mounting none on /dev failed No such device

that is - after the grub2 screen. before the plymouth screen - which shows up for only a moment before gdm kicks in. ie - i have this message for most of the boot processes.

it does not seem to affect the system after everything is loaded.

thanks

Check your ***fstab*** for any inconsistencies. If something in grub was pointing to the wrong device you wouldn't be able to boot.

---

### Post by zika on 2010-03-22
That message is present here for quite some time, I think even in Karmic...

---

### Post by keybuk on 2010-03-22
You would only see this error if you were not running a 2.6.32 kernel - make sure your kernel is the right version for Lucid (some bits might not work with an older kernel).

That being said, it's completely harmless; the error means that it couldn't mount the "devtmpfs" filesystem on /dev - but it will have fallen back to an older, slower, type of /dev

---

### Post by zika on 2010-03-22
> **keybuk said:**
> You would only see this error if you were not running a 2.6.32 kernel - make sure your kernel is the right version for Lucid (some bits might not work with an older kernel).

That being said, it's completely harmless; the error means that it couldn't mount the "devtmpfs" filesystem on /dev - but it will have fallen back to an older, slower, type of /devYou're totally right! I see that only when booting with 2.6.34...

---

### Post by keybuk on 2010-03-22
> **zika said:**
> You're totally right! I see that only when booting with 2.6.34...

2.6.34 has devtmpfs, when you built the kernel did you make sure to set CONFIG_DEVTMPFS=y ?

---

### Post by Irihapeti on 2010-03-22
Thank you. That's another error message that I can disregard. (If that sounds sarcastic, it isn't meant to.)

I'm booting with the Karmic kernel on my desktop PC because it won't boot with Lucid kernels. Yes, I have a bug report filed.

---

### Post by Vanishing on 2010-03-22
> **keybuk said:**
> 2.6.34 has devtmpfs, when you built the kernel did you make sure to set CONFIG_DEVTMPFS=y ?

i tested, in ubuntu kernel ppa, both 33 and 34 kernels have this output during startup. Haven't tested compiling by myself though.

---

### Post by mikio on 2010-03-23
yes, it was due to loading the wrong kernel. i was not aware of this. it happened because my upgrade to lucid failed half way through.. i have installed the lucid kernel and all is fine now.

thank you!

---

### Post by ViperScull on 2010-03-23
happened as well when i compiled .33.1 myself (although i used .config from .33 ubuntu build, plus some changes).

---

### Post by keybuk on 2010-03-23
> **Vanishing said:**
> i tested, in ubuntu kernel ppa, both 33 and 34 kernels have this output during startup. Haven't tested compiling by myself though.

The mainline kernels in the PPA are built using the karmic kernel config, not the lucid kernel config.

This is because they're mostly intended for people reporting bugs on stable releases to find out whether an upstream update will fix the issue (and thus requires little-to-no effort to fix for the next Ubuntu release).

Unfortunately this does mean that they're not suitable for running on the current development release, since the config may be different.

---

### Post by zika on 2010-03-23
> **keybuk said:**
> Unfortunately this does mean that they're not suitable for running on the current development release, since the config may be different.Is it dangerous to use them on development release, due to the difference in config, You mention, and, if it is, what is the danger? I'm asking this because, for more than a year now, I'm always on current from mainline... On, Jaunty, Karmic, Lucid, almost always in testing...

---

### Post by Vanishing on 2010-03-23
> **keybuk said:**
> The mainline kernels in the PPA are built using the karmic kernel config, not the lucid kernel config.

This is because they're mostly intended for people reporting bugs on stable releases to find out whether an upstream update will fix the issue (and thus requires little-to-no effort to fix for the next Ubuntu release).

Unfortunately this does mean that they're not suitable for running on the current development release, since the config may be different.

I see..is there any ppa for development releases?

---

### Post by keybuk on 2010-03-23
> **zika said:**
> Is it dangerous to use them on development release, due to the difference in config, You mention, and, if it is, what is the danger? I'm asking this because, for more than a year now, I'm always on current from mainline... On, Jaunty, Karmic, Lucid, almost always in testing...

It's rarely dangerous; it's certainly unlikely to eat your disk or anything, but I'd certainly keep the actual lucid kernel around in case it turns out that it won't boot with the mainline one.

---

### Post by zika on 2010-03-23
> **keybuk said:**
> It's rarely dangerous; it's certainly unlikely to eat your disk or anything, but I'd certainly keep the actual lucid kernel around in case it turns out that it won't boot with the mainline one.Of course. I, just, always have a current installed... Thank You. There were situations where I could not boot into daily kernel. But rarely...

---

### Post by markackerman8@gmail.com on 2010-04-17
Hi, I think I am pooched!!

Yep the same error in 2.6.33, and simply a blackscreen with a cursor in 32.  Simply stated here is what led up to it.

1/ While compiling the 33 kernel I accidentally closed terminal and it stopped inappropriatley. 
2/ I treid to install it anyway and it installed with errors, and wouldn't load after a restart,
3/ removed said kernel and re-compiled and re-installed it without error.
4/that wouldn't load either, so back to 32 and ununstalled then found the debs and installed the 3 pertaining to 2.6.33, awe4some no compiing!,  
then this and nothing even in safe mode will load.

I guess a reinstall is due,

Are the kernel deb packages safe usually?

---

