---
title: "Desktop takes 2-3 minutes to appear"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by YosefKaro on 2009-12-12
Is anyone else having this problem in Lucid?  Every time that I start up, I have to wait for a few minutes before my desktop with its icons, etc. appears.  How can I solve this problem?

-Yos

---

### Post by ranch hand on 2009-12-12
Well  I certainly do not have that problem.  I have not timed it but I believe it is about 40 seconds from when I select the OS in grub to working desktop, including logging in.

For anyone to help you with this there will have to be a lot more information.  The specs of your box, including video card, and how you installed the OS and what else is on the drive(s).

---

### Post by VMC on 2009-12-12
> **YosefKaro said:**
> Is anyone else having this problem in Lucid?  Every time that I start up, I have to wait for a few minutes before my desktop with its icons, etc. appears.  How can I solve this problem?

-Yos
Mine is around 30 seconds, from grub to desktop.

Output: ```
sudo fdisk -l
```

---

### Post by ubername on 2009-12-12
Just started having this problem (or similar - my desktop has not yet appeared, and I can't launch nautilus - just get the spinning wheel thingy)

edit: running nautilus from terminal gets

(nautilus:2323): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

** (nautilus:2323): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2323): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2323): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault

---

### Post by ubername on 2009-12-12
Thunar show the Desktop folder and all contents
Desktop still has not appeared.

---

### Post by dino99 on 2009-12-12
> **ubername said:**
> Just started having this problem (or similar - my desktop has not yet appeared, and I can't launch nautilus - just get the spinning wheel thingy)

edit: running nautilus from terminal gets

(nautilus:2323): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

** (nautilus:2323): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2323): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2323): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault

have these warnings since October on Karmic & now with Lucid too. :o

---

### Post by ubername on 2009-12-12
nautilus[4437]: segfault at 7f6f50812fe0 ip 00007f6f584e1420 sp 00007f6f50813008 error 6 in libc-2.10.2.so[7f6f58468000+166000]

appears in syslog whe attempting to start nautilus

---

### Post by ubername on 2009-12-13
See [http://ubuntuforums.org/showthread.php?t=1353375](http://ubuntuforums.org/showthread.php?t=1353375)

---

