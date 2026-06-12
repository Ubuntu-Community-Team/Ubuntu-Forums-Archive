---
title: "Weird problem installing kubuntu"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by Wobbley on 2008-04-09
I am pretty new to linux but decided to give it a serious go. So i partitioned my disk and divided it like this: 20gb to Vista, 20gb to linux, 5gb to swap and rest storage. 

I installed ubuntu tried that for about 2 weeks, wanted to try something else went to linux mint tried that for about two weeks and now i wanted to try a KDE desktop so went for kubuntu.

Like always i burned the iso on a disk put it in set boot priorety to CD then the weird stuff happens. When the screen comes up with the choices such as "Start or Install Kubuntu" nothing works. I mean i can move the keys i can press F1 or F2 but i cant actually select any of those options.

Anyone been around this issue? :S

P.S I swear to god linux hates me every installation something weird was going on :( (Could it be cause i am using a re-writable disk where i keep the linux distro i am using?)

---

### Post by Pumalite on 2008-04-09
Do md5sum on your iso, burn at 4x or less on CD-R, check CD integrity after burn and before install.

---

### Post by Wobbley on 2008-04-10
Thanks puma i did an md5sum check and the file seemed to be the issue, Although my problems ain't over yet :(

I installed it and was updating it when i got an error then was telling me that "There was an error committing changes. Possibly there was a problem downloading some packages or the commit would break packages" Right after it tells me that a new distribution is available so i figured i should give that a go. I started there and it stopped when it was going to install the update and was just stuck at 0%. I mean is there even an update as far as i know 7.10 is the latest except the beta?

Anyways i reboot it and what happens is that kubuntu breaks :S So i have to reinstall it, well not necessarily breaks but i cant enter it visually anymore only get a console.

---

### Post by Pumalite on 2008-04-10
Memory? Graphics?

---

### Post by Wobbley on 2008-04-11
Forgot to mention that i activated those restricted drivers or whatever they are for the graphicscard

my system:
8800 GTX
4 GB 4-4-12 800Mhz ram (2 x 2gb)
Q6600

---

### Post by Pumalite on 2008-04-11
You need to install with the Alternate CD and configure your xserver at the end of the installation.
Some people have had luck editing boot (F6) and adding acpi=off irqpoll at the end of the line.(after removing 'quiet splash')

---

### Post by Wobbley on 2008-04-11
Thanks il download it and give it a go :)

---

