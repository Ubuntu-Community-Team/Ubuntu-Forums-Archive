---
title: "ubuntu keeps becoming unbootable shortly after installing"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by mkanmori on 2016-11-11
Hi,

My dell t5400 has issues running Ubuntu. After install all is okay no errors then soon after it will fail to boot, I get black screen after grub and blinking curser. I can never find out the reason why. Also, the ctrl + alt + f1 doesn't work and none of the methods to get into the command line work.

How can I troubleshoot this? Each time I must reinstall it but the os seems fine after that so I have nothing to go on.

Thanks

---

### Post by howefield on 2016-11-11
Thread moved to the "*Installation & Upgrades*" forum.

---

### Post by bearlake on 2016-11-11
Have you checked the HDD for errors?

[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html)

---

### Post by ian-weisser on 2016-11-11
How many reboots until it fails?

---

### Post by mkanmori on 2016-11-12
not sure 10 or more. If I go advanced mode I can get the os to boot, what should I run to find out the cause?
thanks

---

### Post by ian-weisser on 2016-11-12
There's nothing you can 'run' to find out the cause yet.
You have not provided enough information yet to isolate if it's a hardware fault, software fault, partitioning fault, grub fault, or something else, so we're playing 'twenty questions'.
Nobody else has this problem, so it's something specific to your system...

Is your system set to dual-boot with another OS?
Do you have an answer to bearlake's question?

---

### Post by mkanmori on 2016-11-12
thanks, its dual booted with windows 10 which is on the grub manu (automatically did this). I tried to disable the windows hd on bios but it didn't work. I also did a grub upgrade, nothing changed.

I can't get into the os at the moment, before I could use recovery mode to get it to boot. But I will keep trying to see if the HD has errors. But its a fairly new ssd.
Thanks

---

### Post by ian-weisser on 2016-11-12
Does your system reliably boot to Ubuntu after a Windows session? Or is that when it fails?

---

### Post by mkanmori on 2016-11-12
Yer i fails every time after a restart. After a fresh install it would work okay for a while, yer about 10 or more restarts.

I can't get into the os atm - nothing. 

thanks!

---

### Post by mkanmori on 2016-11-12
okay I got into os again from recovery mode. The hd status is disk is ok, smart data and self-tests all ok.

thanks

ps. I have an nvidia gt730 inside the pc (dell t5400) which could be causing this perhaps, but its using the latest nvidia driver 367.59.

---

### Post by wildmanne39 on 2016-11-12
Read only happens uaually when there is a drive issue, I suggest you run a disk check.

---

### Post by mkanmori on 2016-11-12
Ah, 

I used an older nvidia driver (340) and it booted up without issue. That's why!

thanks bearlake and ian.

---

### Post by bearlake on 2016-11-13
> **mkanmori said:**
> Ah, 

I used an older nvidia driver (340) and it booted up without issue. That's why!

thanks bearlake and ian.

Should go back to "thread tools" above your 1st post and select "solved".

I'm sure it will help others. :)

---

