---
title: "too much time taken to display dual boot option..."
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by matrunner on 2007-06-12
hi

         i am a new ubuntu user....actually i have a dual boot of ubuntu and xp...

      for past few days i face a strange new prob....

                                     Once system get started it takes over 12secs to display multi boot option of UBUNTU 7.04 and XP..... i just added a CD-Rom drive to my pc....but each time on restart it takes over 12secs to display multiboot option....

                              plz help me...

---

### Post by Pumalite on 2007-06-12
> **matrunner said:**
> hi

         i am a new ubuntu user....actually i have a dual boot of ubuntu and xp...

      for past few days i face a strange new prob....

                                     Once system get started it takes over 12secs to display multi boot option of UBUNTU 7.04 and XP..... i just added a CD-Rom drive to my pc....but each time on restart it takes over 12secs to display multiboot option....

                              plz help me...

Ubuntu 7.04 is probably trying to recognize your CD-ROM and probably doesn't find it.

---

### Post by mikewhatever on 2007-06-12
You'll have to edit the 'timeout' section of grub menu
> gksudo gedit /boot/grub/menu.lst
find where it says 'timeout 12' (closer to the top) and change the number to 3. Do not set it to 0. Save the file and exit.

here is what the whole section look like
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10


---

