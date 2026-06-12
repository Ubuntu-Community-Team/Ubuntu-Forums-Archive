---
title: "Ubuntu will not load"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by asker1 on 2011-07-10
i had ubuntu running pretty fine and smoothly for 3 weeks.yesterday i tried installing lubuntu over ubuntu.it went well but not that great and started uninstalling it.it was late at night so i didn't uninstall all the packages(i uninstalled just about the half of it).(durning the installation of lubuntu it made me choose windows manager and i chose lxdm)
Now i am trying to boot ubuntu but i can't.It will just stay at the ubuntu startup screen( [IMG]http://1.bp.blogspot.com/_JSR8IC77Ub4/S6747n_wyWI/AAAAAAAAAVg/rcQ7UyAJluw/s400/ubuntu_boot.jpg[/IMG] )
It will load and load and load and just don't stop loading.
If i press any of the arrows,it will get me to the boot proccess log.There, the only failures are two "crash reports"(something like that) and the last line says(i think):stopping V system(i don't remember exactly.can you help me?

Also: my partitions are 434 GB(windows xp) and 66 GB for ubuntu.
if you need anything tell me.

---

### Post by westie457 on 2011-07-10
Try reinstalling again and when you get to the screen that asks what you want to do select the last option which is called advanced  'something else'. This takes you to the partitioning screen where you can choose to install to. Select the linux partition labelled EXT 2,3 or 4 depending on the previous install.
Then in the window that opens you will be making 3 or 4 partitions.Change the size down to 5 GB, this will be root.There will be a box with DO NOT USE THIS DEVICE or something very close. Click on it and select a different choice USE AS EXT 3 or EXT 4. Then mark the small box to format the partition. Under that is a box with USE AS click here and in the drop down select / . With the remaining space in the partition use about 15 GB. This will be used as /boot. If you already have a swap partition use all the remaining space and call it /home.  If no swap then leave about 2 GB and mark this as swap. Exit this window accept and write the changes and the install will go ahead. you will be up and running once the install finishes.

---

### Post by asker1 on 2011-07-10
thanks for it but i don't want getting into reinstalling.
i logged in from recovery mode-low graphics and work fine btw.
maybe i should get my bootfiles to default?

---

### Post by westie457 on 2011-07-10
The only reason I suggested the reinstall was because your system could have been completely screwed and would need doing anyway. Glad you got working. By the way installing any Ubuntu over the top of another one usually wipes the system files and keeps your /Home folder intact. It is the rare cases when the install does its own thing and totally wipes the root partition. If your home folder is inside that partition - good bye to files. That is the reason for the separate home partition. And also a very good reason to have them backed up elsewhere.

Welcome to the Forums.

Any questions that you need answering come back and start a new thread.

---

### Post by asker1 on 2011-07-10
ok i will try normal boot now.
another question off-topic,how can i get on ubuntu a similar to windows - Restore tool?


FINALLY THE PROBLEM PERSISTS,if i login from normal mode the same will happen.if i try recovery mode>low graphics it will run like a charm.
what should i do to fix this?

---

