---
title: "Swap?"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by OpenSourceRules on 2012-06-08
Although I rarely ever reaches 1G of the 2G of RAM on my laptop, swapless installations usually result in slow or unstable system.

I guess swap is not only used to back up RAM, it is used as a stabilizer, too.

---

### Post by wilee-nilee on 2012-06-08
> **OpenSourceRules said:**
> Although I rarely ever reaches 1G of the 2G of RAM on my laptop, swapless installations usually result in slow or unstable system.

I guess swap is not only used to back up RAM, it is used as a stabilizer, too.

You can change the swappiness.

---

### Post by Blackbird_13 on 2012-06-08
To change "swappiness":
```
gksudo gedit /etc/sysctl.conf
```Search for *vm.swappiness* and change its value as desired. If *vm.swappiness* does not exist, add it to the end of the file like so: 
```
vm.swappiness=10
```Save the file and reboot. 
swappiness can have a value of between 0 and 100
swappiness=0 tells the kernel to avoid swapping processes out of physical memory for as long as possible
Source: 
[HTML]https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F[/HTML]I always set swappiness=0

---

### Post by gnorb on 2012-06-08
Thanks for the swapiness information and link!

I had a look at the swap usage yesterday. Due to the reason that my 10" Acer Aspire One, now upgraded to 12.04 with unity, is very slow when switching between users.

The 1G RAM is near used up with only one user logged in and the swap seems unused. Still with two users the situation looks to be the same.

Shouldn't swap be in more active use while switching between users?

---

### Post by Blackbird_13 on 2012-06-08
I'm using just over 400MB at the moment, which is pretty usual for me. Do you know what is using up your RAM?
Since installing 12.04 I find my system very slow switching between users. This was not the case in lucid.

---

### Post by gnorb on 2012-06-12
Changed swapiness from 60 to 10 now. The usage may feel a bit faster but I haven't been able to measure the difference, just watching free & top now and then.

Actually the /etc/sysctl.conf file didn't include the swapiness line by default. Just added the line to the end.

Looking more closely, the high memory usage was just reserved buffered & cache. At least this has confirmed that the slow 12.04 unity on my laptop is not depending on memory size now.

---

