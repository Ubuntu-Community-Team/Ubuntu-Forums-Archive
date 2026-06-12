---
title: "Swap partion usage... help needed..."
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by Moodel on 2006-03-13
I'm fairly new to Linux so please bear with me :)

Well I wont go into how or why I did it but suffice to say I deleted my Swap partition from my config.

Anyway I managed to get it back and entered correctly in the fstab file but I have a question...

If I run the following "cat /proc/swap" it shows me that my swap space is running at -1 priority.......reading through various explanations for the swapon command it would appear that this priority should be between 0 - 32767.

So how do I change it?....and why would it be running with a priority of -1?

I know you can run Linux without a swap partition but I only have 512Mb and after some time of running my machine slows right down and I have to reboot :(

Thanks :)

---

### Post by psusi on 2006-03-13
Ignore the priority; it only comes into play when you have multiple swap devices.  The -1 just means you did not specify any priority.  

[QUOTE=Moodel]I'm fairly new to Linux so please bear with me :)

Well I wont go into how or why I did it but suffice to say I deleted my Swap partition from my config.

Anyway I managed to get it back and entered correctly in the fstab file but I have a question...

If I run the following "cat /proc/swap" it shows me that my swap space is running at -1 priority.......reading through various explanations for the swapon command it would appear that this priority should be between 0 - 32767.

So how do I change it?....and why would it be running with a priority of -1?

I know you can run Linux without a swap partition but I only have 512Mb and after some time of running my machine slows right down and I have to reboot :(

Thanks :)[/QUOTE]

---

