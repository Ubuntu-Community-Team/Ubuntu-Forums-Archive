---
title: "USB Boot time"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by jow21 on 2007-08-07
Hello there,

I have installed Ubuntu 7.04 on an USB-key and it all works perfect - my only problem is the boot time is + 3 minutes compared to 40 seconds when booting from the harddisk on the same computer (USB 2.0 is used).

I have tried to trim what services to load (BootManager) but it has only decreased the boot time with maybe 10 seconds.

Does anyone have any experince with, or oppinon about, if it is an expected boot time from an USB-key? 

Any suggestion for reducing boot time will of course be of great interest!

Kind regards
Jens

---

### Post by jnorthr on 2007-08-07
Is the swap file on the key as well ? There may be a contention issue if swap is being used for a lot of work while o/s loads. It still sounds like a LONG time to me.

---

### Post by kerry_s on 2007-08-07
your limited to 2.0 speed, not much you can do to get past the bottle neck.

---

### Post by jnorthr on 2007-08-07
Perhaps if it's like my machine, the drive is rated 2.0 but your actual port in the machine is only a 1.1 rated which is MUCH slower.

---

### Post by jow21 on 2007-08-09
Thanks for the input so far. 

The swapfile is located at the 4GB USB-key on a seperate partition. There is 1GB RAM in the pc so I don't know if Ubuntu uses the swapfile?

The USB-port is seen as 2.0, but I can follow kerry_s: The USB interface is slower (60MB/s) than the IDE (133MB/s). 

Isolated it will increase the boot time with a factor of app. 2.2 - so it can not totally explain why it takes 40 seconds from an IDE-disk and maybe 200 seconds from an USB-key....

It looks to me like when I boot fra the USB-key it makes a RAM-disk and loads Ubuntu into it and start it from there - anybody that can confirm that. If so it would explain another bit of the time difference. 

Thanks in advanced of your feedback

---

