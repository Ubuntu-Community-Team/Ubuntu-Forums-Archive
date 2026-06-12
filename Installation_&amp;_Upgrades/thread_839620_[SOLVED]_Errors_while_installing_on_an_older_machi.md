---
title: "[SOLVED] Errors while installing on an older machine!!"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by swoody on 2008-06-24
I'm having some problems trying to install Ubuntu on my Windows 98 comp. It's running an 8gb IDE harddrive, Pentium II, and 96mb RAM. I know the install disc is good since I used it to install Hardy on my laptop.

I tried acpi=force, noacpi, and acpi=off, but it's not working. When I try acpi=force, it still gives me the same error message, when I try noacpi or acpi=off it'll start the bootsplash, but will wind up freezing with the lights on my keyboard flashing. I finally got it to get past the ubuntu splash screen, but only to have my monitor flooded with error messages that keep coming:

SQUASHFS error: Unable to read fragment cache block 0xa4cff
SQUASHFS error: Unable to read page, block 2933658b, size 989b
SQUASHFS error: sb_bread failed reading block 0xa4cff
 
Please, if anyone has any ideas or tips, they would be greatly apppreciated. Thank you all very much!

-Woody

---

### Post by avtolle on 2008-06-24
It's not going to install on only 96 mb of Ram.

---

### Post by swoody on 2008-06-24
> **avtolle said:**
> It's not going to install on only 96 mb of Ram.

How much would I need to be able to install it?

---

### Post by avtolle on 2008-06-24
From the "alternate install" text based installer disk, 256mb minimum; from the Live (Desktop)CD, 384 mb (the difference is to allow the graphical installer to run). There are a few options available to you other than full-fledged Ubuntu, but which are based upon Ubuntu. At 96 mb, I'd suggest doing a minimal installation, with a "light" window manager installed, such as Fluxbox, IceWM. I understand there is something known as Ubuntulite in the works, the details of which are unknown to me. 

There is also the possibility of doing a minimal install of Debian with a light-weight DE on top, there is Puppy Linux, DSL (Damned Small Linux), and a few others.

EDIT: A link to installation on low-memory systems, if you are interested: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by swoody on 2008-06-25
> **avtolle said:**
> From the "alternate install" text based installer disk, 256mb minimum; from the Live (Desktop)CD, 384 mb (the difference is to allow the graphical installer to run). There are a few options available to you other than full-fledged Ubuntu, but which are based upon Ubuntu. At 96 mb, I'd suggest doing a minimal installation, with a "light" window manager installed, such as Fluxbox, IceWM. I understand there is something known as Ubuntulite in the works, the details of which are unknown to me. 

There is also the possibility of doing a minimal install of Debian with a light-weight DE on top, there is Puppy Linux, DSL (Damned Small Linux), and a few others.

EDIT: A link to installation on low-memory systems, if you are interested: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Thank you so much! I don't have the time to look through it all right now, but I'll check it all out first thing in the morning. I really appreciate the help!

---

### Post by Partyboi2 on 2008-06-25
[[COLOR=Blue]Here is a another useful link[/COLOR]]("http://www.psychocats.net/ubuntu/minimal#barebones")

---

### Post by swoody on 2008-07-03
Thanks guys! I did the minimal disc, and downloaded everything as I went.

---

