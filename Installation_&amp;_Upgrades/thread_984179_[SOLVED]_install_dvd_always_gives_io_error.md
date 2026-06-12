---
title: "[SOLVED] install dvd always gives i/o error"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by penguin_shep on 2008-11-16
hi there,
i'm completely new to linux and decided to burn a dvd of 8.10 to put on a fresh hard drive because it looks awesome.

i used this dvd at school to run the livecd mode and it worked like a charm, but when i put it in my computer and select install ubuntu or try to run the live cd it always pulls up the screen with the ubuntu logo and that orange bar bouncing back and forth, then it starts showing all of the following errors repeatedly in random order:

```
end_request: i/o error, dev sr0, sector 48
buffer i/o error on device sr0 locical block 0
end_request: i/o error, dev sr0, sector 48
buffer i/o error on device sr0 locical block 1
end_request: i/o error, dev sr0, sector 48
buffer i/o error on device sr0 locical block 2
end_request: i/o error, dev sr0, sector 48
buffer i/o error on device sr0 locical block 3
end_request: i/o error, dev sr0, sector 48
buffer i/o error on device sr0 locical block 4
end_request: i/o error, dev sr0, sector 48
buffer i/o error on device sr0 locical block 6
end_request: i/o error, dev sr0, sector 0
buffer i/o error on device sr0 locical block 0
```

i searched forums for hours trying to find the same error, and the closest thing i found involved removing the cd from the drive. but that can't work  because i need to install it off of the dvd.

help is immensely apprecieated. :)

---

### Post by oldos2er on 2008-11-16
Looks like it may be corrupt. Try running 'Check CD for defects' from the startup menu.

---

### Post by penguin_shep on 2008-11-16
> **oldos2er said:**
> Looks like it may be corrupt. Try running 'Check CD for defects' from the startup menu.

i ran check cd for defects just like you said, but it didn't even make it that far. just got to the bouncing orange bar again and then more errors, but with different numbers:
```
end_request:i/o error, dev sr0, sector 9193976
buffer i/o error on device sr0 logical block 0
end_request:i/o error, dev sr0, sector 1149247
buffer i/o error on device sr0 logical block 1
end_request:i/o error, dev sr0, sector 9193976
buffer i/o error on device sr0 logical block 2
end_request:i/o error, dev sr0, sector 112
buffer i/o error on device sr0 logical block 3
end_request:i/o error, dev sr0, sector 9193976
buffer i/o error on device sr0 logical block 14
end_request:i/o error, dev sr0, sector 112
```

allow me to reinterate that this cd has worked fine on at least 3 other computers. i think it might be hardware incompatibility. is there something i can change in the code by pressing F6 to bypass an error like this perhaps?

---

### Post by oldos2er on 2008-11-16
"i think it might be hardware incompatibility"

 What hardware are you running?

---

### Post by penguin_shep on 2008-11-16
> **oldos2er said:**
> 
 What hardware are you running?


well, it's not like i'm saying i know that is what it is, i just figured that "dev sr0" and "device sr0" might be referring to a piece of hardware in my system linux doesn't particularly like.

but here it all is:
motherboard: **intel d845wn** 800mhz fsb
hdd(s): 37gb **maxtor 6l040j2**, 37gb **samsung sp0401n **
memory: 512mb sdram
disk drive: samsung dvd-rom sd-616
processor: intel pentium 4 @ 1.79ghz

---

### Post by penguin_shep on 2008-11-18
well, after looking around extensively, i figured i'd let you guys know that i found out the problem.

my dvd drive was incompatible with booting dvd's.

all i did was unplug my primary dvd drive, leaving my slave cd rom and reburned the disk to a cd-r and it worked like a charm.

thanks for the help anyway, though.

---

### Post by oldos2er on 2008-11-18
Glad you got it working. Can you please mark this thread as 'Solved'?

---

