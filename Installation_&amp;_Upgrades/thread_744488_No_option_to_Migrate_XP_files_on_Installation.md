---
title: "No option to Migrate XP files on Installation"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by evabehemoth on 2008-04-03
I just tried installing both the AMD64 and the normal version of 7.10 but after the partitioning guide, the installer seems to skip step 5 (migration). I thought it was the fact that I was switching from 32 bit to 64 Ubuntu, but that is not the case.

I only have one hard drive and I want to get rid of my XP partition, but transfer my music and pictures.

Does the Migration feature require a 2nd hard drive?

If not, any assistance as to how to fix this would be much appreciated.

Thanks.

---

### Post by Pumalite on 2008-04-03
You have to backup your movies and pictures and restore them later.
What partition do you want to get rid of?
Post:
sudo fdisk -lu

---

### Post by evabehemoth on 2008-04-03
The XP partition is the only one I have.

Do I have to make a 2nd one?

---

### Post by Pumalite on 2008-04-03
Do you want to erase XP and install Ubuntu or do you want to shrink XP and install Ubuntu in dual boot?

---

### Post by ajgreeny on 2008-04-03
You can only migrate your XP bits and pieces when you go to a dual boot.  If you chose a complete install and remove XP at the formatting stage there is nothing to import.  Remember, however, that the import does not move all your documents etc etc over, only your configuration of Internet Explorer or Firefox and emails etc.  All your movies, docs and music will need moving manually.

---

### Post by evabehemoth on 2008-04-03
Alright. Just needed that clarified.

Thanks to you both.

---

