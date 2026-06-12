---
title: "updated ubuntu from 12.04 to 14.04, dmesg still says precise"
date: 2016-03-12
forum: Installation &amp; Upgrades
---

### Post by fengjiahai on 2016-03-12
Hi, I upgraded from 12.04 to 14.04 a few months ago, but recently when I checked my linux headers from uname -r, I realised that it's on 3.5.0-52-generic, which apparently is a kernel for 12.04. As a result, I also wasn't able to apt-get the relevant linux headers.

I also tried to verify this using dmesg, which gives:

```
Linux version 3.5.0-52-generic (buildd@kissel) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #79~precise1-Ubuntu SMP (Ubuntu 3.5.0-52.79~precise1-generic 3.5.7.33)


```

Is this normal? Should I just grab the header files from another repository or is this a fundamental problem that I should address, by changing kernel or something?
If so, how do I go about changing the kernel?

---

### Post by v3.xx on 2016-03-12
```
inxi -S
```

What will that output?

---

### Post by ajgreeny on 2016-03-12
If inxi is not installed, and it did not used to be, show us also the output of ```
lsb_release -dc && echo "Desktop:	$DESKTOP_SESSION" && uname -mrn
``` which will show similar output to the **inxi -S** command

---

### Post by v3.xx on 2016-03-12
May not even be a bad idea to have a look at your sources.

```
inxi -r
```

or
```

cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

### Post by deadflowr on 2016-03-12
Possible grub never updated.
Is it a single boot or dual/multi-boot system?

If dual/multi-boot, perhaps grub installed on a different system is the grub in charge, and until that gets updated, it'll always point to the grub setting it has in place.
Meaning it'll keep loading the old kernel.

Currently, though, we are all swinging at random pitches.

---

