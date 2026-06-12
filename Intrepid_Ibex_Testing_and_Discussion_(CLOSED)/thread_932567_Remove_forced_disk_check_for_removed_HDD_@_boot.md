---
title: "Remove forced disk check for removed HDD @ boot"
date: 2008-09-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LavianoTS386 on 2008-09-28
I removed a HDD that had a forced disk check on it. I was testing the drive before I sent it off to an ebay buyer, so I don't have the disk anymore. 

Now in the middle of the boot, the splash screen turns to a blank screen and I have to press Ctrl+D for the boot process to resume. How do I remove the reference to check the removed HDD, so that my system can boot normally?

---

### Post by Gina on 2008-09-28
You need to edit **fstab** and remove the entries for any partitions on that drive.

---

### Post by LavianoTS386 on 2008-09-28
Thanks, works perfectly now.

---

