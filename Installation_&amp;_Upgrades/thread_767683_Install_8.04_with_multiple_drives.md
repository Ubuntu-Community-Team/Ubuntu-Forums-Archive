---
title: "Install 8.04 with multiple drives"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by dobrowski on 2008-04-25
I am facing an issue trying to install Hardy Heron. Please bear with me since it is my first install and it may be an obvious error.

I was receiving the /sbin/modprobe error mentioned by others (Thread #585047). I searched and saw it was related to multiple harddrives which I have also.

I tried, using the install disk and hit F6 and then added "all_generic_ide" after the text line that appeared. After hitting enter it seemed to run and then freeze on the splash screen without the orange bar moving back and forth.

Is this typical? A problem with having multiple hard drives? Am I misentering the boot kernel parameter in the wrong way?

Thanks for any guidance.

---

### Post by Pumalite on 2008-04-25
Are they all SATA or mix of IDE and SATA? Are you dual booting? Vista or XP?

---

### Post by dobrowski on 2008-04-25
I think that they are a mix.  I'll check.  A friend built the computer for himself and then gave it to me when he left the country.  

I want to dual boot XP and Ubunutu, but XP isn't working right now either.  So if I could just get one OS working and then the other I'd be happy.

---

### Post by dobrowski on 2008-04-25
They are one 240 GB SATA, then two IDE drives (120 GB, 200 GB)

---

### Post by Pumalite on 2008-04-25
I recommend you use the first drive for a clean install of XP first followed by clean install of Ubuntu. Leave the other drives for storage or separate /home.

---

