---
title: "Freezing on Latest Kernel 2.6.31.12"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by skillllllz on 2009-10-07
I upgraded to the latest kernel today, 2.6.31-12.40, and now my Dell Inspiron 1420n makes it past grub and then locks up hard on a blank screen. How do I go about troubleshooting this? I can boot up and operate just fine on 2.6.31-11.38.

---

### Post by Sslaxx on 2009-10-07
Getting it to boot in verbose mode might help.

---

### Post by skillllllz on 2009-10-07
I am not exactly sure how to do so in GRUB2; there is no menu.lst in /boot/grub/

What should I do?

---

### Post by andresmh on 2009-10-07
I am also experiencing the same thing. When booting with 2.6.3.12 I get to the login window but then it freezes. Things are fine when I use 
Linux karmicx300 2.6.31-11-generic #38-Ubuntu SMP Fri Oct 2 11:55:55 UTC 2009 i686 GNU/Linux

---

### Post by VMC on 2009-10-07
Hey guys, what's the output of this ```
lspci|grep VGA
```

---

### Post by kansasnoob on 2009-10-08
I was experiencing freezes with the new kernel and legacy grub, so I flipped back to grub2 (aka:grub-pc) and all seems happy so far.

I'm going to post my "sample" grub "flipping" how-to soon.

---

### Post by skillllllz on 2009-10-08
> **VMC said:**
> Hey guys, what's the output of this ```
lspci|grep VGA
```

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)

---

### Post by VMC on 2009-10-08
> **skillllllz said:**
> 01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)

I take it that you installed the latest nVidia drivers and it's just when you installed the latest kernel that it froze, correct?

By the way there is a newer point issue kernel 2.6.31-12.41 I just received on updates. Couldn't find any change log to report.

---

### Post by skillllllz on 2009-10-08
Yes, I've had the latest nvidia driver (183) installed since the beta was released. It was only after upgrading to the latest kernel that the freezing began.

I see the newer point issue kernel and am upgrading as I type this. The changelog does not mention anything about this particular issue; it looks like it addresses the very laggy performance some intel graphics users were seeing after the last kernel update.

---

### Post by skillllllz on 2009-10-08
Well, I haven't had anymore freezing since the last update last night. The fix must have been included in it.

---

### Post by skillllllz on 2009-10-08
Nope, it's still happening. It doesn't happen every single time it boots. I removed "quiet splash" from the grub config to see where it hangs. Right before it hangs it says something about a "Call Trace" and
"recover from recursive loop, but require reboot" and then the screen goes blank. It does this about 7 out of ten reboots. The other times it boots right in but seems slower than the previous kernel. Any ideas?

---

### Post by emarkay on 2009-10-08
Skilllz, what exact Graphics card do you have, and is it an AGP (older) card?

---

### Post by skillllllz on 2009-10-08
This is from lspci

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)

Being that this is the onboard video of my Dell Inspiron 1420n laptop, I'm not exactly sure if it's utilizing AGP or not.

---

### Post by andresmh on 2009-10-08
It's not happening to me anymore after doing aptitude full-upgrade.

---

### Post by Longinus00 on 2009-10-09
> **skillllllz said:**
> This is from lspci

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)

Being that this is the onboard video of my Dell Inspiron 1420n laptop, I'm not exactly sure if it's utilizing AGP or not.

If it's still happening, try removing the nvidia driver for awhile and just use the nv driver. If that fixes it you can go ahead and try reinstalling the nvidia driver.

---

