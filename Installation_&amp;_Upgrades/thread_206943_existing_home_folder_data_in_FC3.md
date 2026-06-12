---
title: "existing home folder data in FC3"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by travise on 2006-06-30
After messing about with my wireless card in FC3 for over a week, I tried the ubuntu live cd and the thing was supported no problems, no questions. 

Naturally, I plan to install the ubuntu as soon as i find out the following: if the machine is already a linux machine (as mine is), will the installation repace out the kernal and the components, or will it re-partition and re-format the whole filesystem?

in other words, do i need to back up all my \home folder stuff, or will it wurvive the ubuntu installation? (the machine in question is a bit old with only a slow cd burner, and a backup would be pretty consuming)

thanks, 

travis e

---

### Post by soce_32 on 2006-06-30
As long as you don't let the install process do the auto-partitioning, and your home data is on its own partition, you won't have to back it up.

When it comes to setting the disk up, choose manual or expert mode.  You will want to mark all of the partitions except for your home partition to be formatted.  When you boot into ubuntu, you should see all of your data in your home folder.

If you do not have a separate home partition, you will need to back it up.

---

