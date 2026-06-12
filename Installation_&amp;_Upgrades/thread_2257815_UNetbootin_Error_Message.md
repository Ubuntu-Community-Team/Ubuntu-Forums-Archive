---
title: "UNetbootin Error Message"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by Kurt_Alan on 2014-12-22
Does anyone have a fix for this UNetbootin error: ```
 Failed to load COM32 file menu.c32 
```

---

### Post by vasa1 on 2014-12-22
[https://bugs.launchpad.net/unetbootin/+bug/1190256](https://bugs.launchpad.net/unetbootin/+bug/1190256)

---

### Post by Kurt_Alan on 2014-12-22
@vasa1

Thanks for this.  Thus far this solution did not work: ```
lucas@lucas-desktop:/usr/lib/syslinux/modules/bios$ sudo cp libutil.c32 libcom32.c32 menu.c32 /media/lucas/186ac1ea-de5c-49bc-abca-5ab883fb2e09/boot/grub/ 
```

Still reading through this thread for other clues.

---

### Post by Kurt_Alan on 2014-12-22
I re-read the thread and found a solution:

So the same as before (See post re: moving of files). Then after booting and halting at error message, hit Tab.  A list of boot options will appear.
Type ```
 unetbootindefault 
``` and hit Enter.  The new "live" OS will load.

In this thread, the only people who were not finding a solution were running Ubuntu 14.10.  This last step solves the problem for Xubuntu 14.10, 64 bit, at least for me.

Comments: I upgraded from 14.04 LTS to 14.10, both Xubuntu.  Since that upgrade, the problems have been mounting: a. mouse cursor grabs icon when dragging, b. About Me picture disappears after restart, c. Aboout Me no longer functions, d. Menu Favorites disappear after restart, e. Dropbox indicator fails.  So I will now re-install 14.04 LTS (Xubuntu) and hope for improvement.

---

### Post by Bucky Ball on 2014-12-23
Well, 14.10 has about 7 months support remaining while 14.04 LTS is supported until April 2019 so might be preferable, depending on how you work. I run the LTS releases and have three spare partitions for playthings (like interim releases and other OSs). Good luck. ;)

---

### Post by sudodus on 2014-12-23
Several tools and tips are described in the following link. Unetbootin is one of the tools that often works.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

I agree with *Bucky Ball*, that it is a good idea to run the LTS versions and skip the 9-month versions, so 12.04 LTS and 14.04 LTS (and in the future 16.04 LTS to be released in April 2016 ...)

---

### Post by Bucky Ball on 2014-12-23
You've marked this thread as solved. Presuming you have reinstalled 14.04 LTS and all is good. Please share. Thanks. ;)

---

### Post by Kurt_Alan on 2014-12-23
Hi Bucky Ball,

I read one of the first books on the bucky ball years ago when this molecule was discovered. It's led to many, many advances, as you know. Yes, I'm jazzed by your idea of dual booting. Now that I have a 256 GB ssd instead of the 8 GB ssd I had on my Dell mini-inspiron, I'm thinking of running 14.04 LTS  as my primary OS utilizing, say, 150 GB, then 50 GB for Linux Mint, 17.1 MATE to play movies "out of the box," then 50 GB free space for playing around, like checking out Arch Linux.  I think this is the way to go.

---

### Post by Kurt_Alan on 2014-12-23
In the process of re-install. I will report back. Let's see how many of my 14.10 problems will be resolved, or not, by 14.04. I know there is a thread a 14.10 upgrade experiences.

---

### Post by Kurt_Alan on 2014-12-23
@Bucky Ball -- This thread was marked "solved" not because I solved my 14.10 problems but because I solved my UNetbootin problems so that I could solve my 14.10 problems -- wheels within wheels!

---

