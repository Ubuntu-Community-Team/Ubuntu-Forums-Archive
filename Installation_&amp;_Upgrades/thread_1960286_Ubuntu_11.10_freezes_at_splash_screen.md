---
title: "Ubuntu 11.10 freezes at splash screen"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by Jerry M on 2012-04-17
Hello,

I have been using ubuntu 11.10 for 3 months now. However, suddenly after installing the latest updates the desktop PC freezes at splash screen. I tried to disable graphics and get tty1 but when i try to restart graphics it stucks. My graphic card is NVIDIA GeForce 6600 GT (rev a2).
Could you please guide me with how to troubleshoot this issue.

Thanks,

Jerry

---

### Post by Jerry M on 2012-04-17
Here are the last three  messages from the system before it freezes:
 * Starting Bluetooth OK
* PulseAudio configured for per-user session
saned disabled; edit /etc/default/saned
* Checking battery state.... OK



 Does that make any sense to anyone? 

PS. Ubuntu is the only OS currently installed at my desktop

---

### Post by bogan on 2012-04-17
Hi! **jerry M**,

There are several threads reprting similar difficulties following the recent updates to the nvidia-current driver. see for instance my post:[http://ubuntuforums.org/showthread.php?p=11844097&posted=1#post11844097](http://ubuntuforums.org/showthread.php?p=11844097&posted=1#post11844097)

> * Checking battery state.... OK This usually means video driver problems.

Chao!, **bogan**.

---

### Post by Jerry M on 2012-04-17
Thanks for your reply bogan, indeed it was a video card driver problem.
I had to run the following command

```

sudo dkpg --configure -a
```

which among others updated my current nvidia driver.

I also found the following helpful

[http://ubuntuforums.org/showpost.php?p=11358332&postcount=6](http://ubuntuforums.org/showpost.php?p=11358332&postcount=6)


best,

Jerry

---

