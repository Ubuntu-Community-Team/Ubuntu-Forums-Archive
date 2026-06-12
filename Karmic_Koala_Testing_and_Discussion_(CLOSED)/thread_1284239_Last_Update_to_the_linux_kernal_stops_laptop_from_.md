---
title: "Last Update to the linux kernal stops laptop from booting"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by victor9098 on 2009-10-06
Hi,

I just received and update to the linux kernal within the last hour but after restarting the boot process just freezes on a screen of text. After sometime I have no choice but to do a hard shutdown.

On restarting I am given the option of selecting which linux kernal to use, I choose the older one and the laptop starts up without any problems.

This happen to anyone else?

---

### Post by DougieFresh4U on 2009-10-06
Went to update and was told that there were 'broken packages', being kernel packages, so I didn't update. Sure things will sort out in a while.

---

### Post by victor9098 on 2009-10-06
I got no warning, I used synaptic it got all the updates and installed without an error. Just asked me to restart the system at the end.

Currently using 2.6.31-11-generic. Yes, hopefully there will be another update soon!

---

### Post by joey-elijah on 2009-10-06
> **victor9098 said:**
> Hi,

I just received and update to the linux kernal within the last hour but after restarting the boot process just freezes on a screen of text. After sometime I have no choice but to do a hard shutdown.

On restarting I am given the option of selecting which linux kernal to use, I choose the older one and the laptop starts up without any problems.

This happen to anyone else?

I'm on a desktop, and with this new and the last kernel update i got the same at first. I think a few days afterwards something rolled in and when i tried the newer kernel it booted fine. So, just keep using what works and try the newer one every so often.

---

### Post by slakkie on 2009-10-06
Can you show the output of 

dpkg -l | grep linux-image

and 

uname -a

Thanks.

Never mind, i see you have -11. There were kernel-headers kept back.

---

### Post by raiwo on 2009-10-06
my machine boots & works OK but power manager stopped recognizing my battery like i am all the time on AC, made a bug report on it.

:(

---

### Post by emarkay on 2009-10-06
Was this a "Partial Update"?

---

### Post by kansasnoob on 2009-10-06
> **emarkay said:**
> Was this a "Partial Update"?

No. I've been out quite a bit today but I see some things are somewhat still to be sorted out in updates.

Disc usage is unusually high:

> lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
[COLOR="Red"]/dev/sda3              6.3G   4.9G   1.1G  82% /[/COLOR]
udev                   1.1G   279k   1.1G   1% /dev
none                   1.1G   201k   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              11G   1.6G   8.7G  16% /home


I suggest being patient and seeing if things don't sort themselves out over the next 12 to 24 hours.

---

