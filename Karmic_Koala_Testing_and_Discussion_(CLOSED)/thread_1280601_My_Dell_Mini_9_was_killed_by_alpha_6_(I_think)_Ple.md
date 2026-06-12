---
title: "My Dell Mini 9 was killed by alpha 6 (I think) Please help!"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pHreaksYcle on 2009-10-02
I installed the 9.10 netbook remix from alpha 4, upgraded all the way until alpha 6 at which point it just crashed, and crashed hard. It said there was nothing to boot on the hard disk, and when I tried to boot from live USB, it threw up a GRUB error, either 11 or 13 I believe.

This isn't a fluke thing, it happened to 2 or 3 of my other friends doing the same thing with their Mini's.

I Google'd the issue, and the solution I saw was to boot from a LiveCD rather than a LiveUSB. This worked, I installed, everything was ducky, until I rebooted and tried to boot from the disk. It said BOOTMGR not found, Ctrl-Atl-Del to restart.

You can hit those as many times as you like, it still throws the same error. Someone please help me, I'm begging you, me and my buddy need our netbooks for school and this is killing us academically. Thanks for any help in advance.

---

### Post by psyke83 on 2009-10-02
> **pHreaksYcle said:**
> I installed the 9.10 netbook remix from alpha 4, upgraded all the way until alpha 6 at which point it just crashed, and crashed hard. It said there was nothing to boot on the hard disk, and when I tried to boot from live USB, it threw up a GRUB error, either 11 or 13 I believe.

This isn't a fluke thing, it happened to 2 or 3 of my other friends doing the same thing with their Mini's.

I Google'd the issue, and the solution I saw was to boot from a LiveCD rather than a LiveUSB. This worked, I installed, everything was ducky, until I rebooted and tried to boot from the disk. It said BOOTMGR not found, Ctrl-Atl-Del to restart.


So your netbook is using a dual-boot configuration with Windows? The BOOTMGR error is actually a Windows problem, so I suspect that installing Ubuntu has caused a problem there.

Try to hold the shift (or shift + esc) key while booting to bring up the GRUB menu, and see if you can boot into Ubuntu or Windows using one of those options.

> You can hit those as many times as you like, it still throws the same error. Someone please help me, I'm begging you, me and my buddy need our netbooks for school and this is killing us academically. Thanks for any help in advance.

You're not supposed to run a development release on production-critical systems.

---

### Post by pHreaksYcle on 2009-10-02
> You're not supposed to run a development release on production-critical systems.

I know >_< Haha, we like to push the limit. Cutting edge draws blood sometimes.
> 
So your netbook is using a dual-boot configuration with Windows? The BOOTMGR error is actually a Windows problem, so I suspect that installing Ubuntu has caused a problem there.

Windows has never touched any of these machines. That's why it's so obscure. Getting a GRUB error while booting the flash drives was the strangest thing...because there IS no GRUB on a liveUSB. Right?

Update:
Sorry if this wasn't clear from first post. We have the beta installed currently.
I powered it up to try the shift escape on GRUB thing, and surprisingly it did something differnent. It has given me a recovery menu with resume, clean, dpkg, fsck, etc.

---

### Post by pHreaksYcle on 2009-10-02
I got one of them booted! Somehow, just by rebooting it a whole bunch of times, one time I got lucky and it threw me to a rescue menu, where I selected the "resume" option to boot normally. I am now installing updates on the beta for machine 1. That one should be okay.

However, this machine #2 is reading
```
GRUB loading.
error: file not found
grub rescue>
```

Any ideas? Or just keep rebooting and pray like the last one?

Thanks for your help so far and for letting me bother you.

---

### Post by jlacroix on 2009-10-02
> **pHreaksYcle said:**
> I got one of them booted! Somehow, just by rebooting it a whole bunch of times, one time I got lucky and it threw me to a rescue menu, where I selected the "resume" option to boot normally. I am now installing updates on the beta for machine 1. That one should be okay.

However, this machine #2 is reading
```
GRUB loading.
error: file not found
grub rescue>
```

Any ideas? Or just keep rebooting and pray like the last one?

Thanks for your help so far and for letting me bother you.

Are you sure you don't have a Dell utility partition that Ubuntu doesn't know how to handle?

---

