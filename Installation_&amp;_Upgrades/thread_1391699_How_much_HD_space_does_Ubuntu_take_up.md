---
title: "How much HD space does Ubuntu take up?"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Doc_Jude on 2010-01-27
Okay, I bought a Lenovo T61 off of Ebay, it was listed as having a 250gig HD with Vista installed. After I did a full install of Ubuntu 9.04 from a Ubuntu disk, no partitions, the Disk Usage Analyzer said that I had 217gig available with a little over 2gig used (for Ubuntu, I suppose). So... did I get screwed out of 30gigs of HD space or what?

***good thing I haven't left my Feedback on the Ebay sale, huh?*** ;)

---

### Post by TenPlus1 on 2010-01-27
Check for hidden partitions where the manufacturers keep DVD images so you can restore Vista back onto the hard-drive...  They usually keep a fair size for those and drivers...

---

### Post by Leshrac on 2010-01-27
Also, take into account that the manufacturer most likely labeled the hard drive as being 250 decimal Gigabytes, while most software will show the size of the hard drive in binary Gigabytes (GiB or Gibibyte).

250 decimal Gigabytes only amout to around 232 binary Gigabytes.

See [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion]("http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion")

---

### Post by Cabs21 on 2010-01-27
First of all 250 GB HDD is really only 232.5 GiB (binary) which is what the computer understands. 1's and 0's.  Second ubuntu is taking up 2 to 3 GB of space.  Third depending on your RAM size your swap could be very high.(typically 1.5 times your RAM by default)  SO if you have 8 GB of ram then....

250 GB x 93%(converts GB to GiB) = 232.5 GiB
232.5 GB - 3 GB (Ubuntu space) = 229.5 GB
guessing 8 GB RAM = 12 GB swap
229.5 GB - 12 GB = 217.5 GB of unused space

If you are desperate for the extra 12 GB of HDD space you could turn off your swap but swap is great for when the RAM is overloaded and will usually crash Ubuntu if the RAM fills up and swap is turned off.  I suggest getting a portable or desktop HDD if you have a laptop or installing another HDD if you know how.  Hope that helps

> **TenPlus1 said:**
> Check for hidden partitions where the  manufacturers keep DVD images so you can restore Vista back onto the  hard-drive...  They usually keep a fair size for those and  drivers...

This could equate to around 10 GB of HDD space in a partition that was already created but not reformatted when you installed Ubuntu. 

250 GB x 93%(converts GB to GiB) = 232.5 GiB
232.5 GB - 3 GB (Ubuntu space) = 229.5 GB
229.5 - 10 GB = 219.5 GB
guessing 1 GB RAM =  1.5 GB swap
219.5 GB - 1.5 GB = 218 GB of unused space

---

### Post by Doc_Jude on 2010-01-27
> **Cabs21 said:**
> First of all 250 GB HDD is really only 232.5 GiB (binary) which is what the computer understands. 1's and 0's.  Second ubuntu is taking up 2 to 3 GB of space.  Third depending on your RAM size your swap could be very high.(typically 1.5 times your RAM by default)  SO if you have 8 GB of ram then....

250 GB x 93%(converts GB to GiB) = 232.5 GiB
232.5 GB - 3 GB (Ubuntu space) = 229.5 GB
guessing 8 GB RAM = 12 GB swap
229.5 GB - 12 GB = 217.5 GB of unused space

If you are desperate for the extra 12 GB of HDD space you could turn off your swap but swap is great for when the RAM is overloaded and will usually crash Ubuntu if the RAM fills up and swap is turned off.  I suggest getting a portable or desktop HDD if you have a laptop or installing another HDD if you know how.  Hope that helps



This could equate to around 10 GB of HDD space in a partition that was already created but not reformatted when you installed Ubuntu. 

250 GB x 93%(converts GB to GiB) = 232.5 GiB
232.5 GB - 3 GB (Ubuntu space) = 229.5 GB
229.5 - 10 GB = 219.5 GB
guessing 1 GB RAM =  1.5 GB swap
219.5 GB - 1.5 GB = 218 GB of unused space

Cool! Thanks... this answers some questions.

Wow. I just yelled at a guy over Ebay and added that HD issue to my list of issues (crappy battery, and crappy dirty condition of "Mint Condition" laptop). Too bad I can't take it back.

---

### Post by noletolucas on 2010-10-29
Just installed Ubuntu **10.04 and it takes up: 2.1gib.**

---

