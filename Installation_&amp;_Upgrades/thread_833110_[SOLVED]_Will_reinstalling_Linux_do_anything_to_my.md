---
title: "[SOLVED] Will reinstalling Linux do anything to my Windows partition?"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by Pikestaff on 2008-06-18
Hello, I have been a happy Kubuntu 6.06 "Dapper" user for about a year and a half now-- yes, I never upgraded, because it worked well for me and because newer versions have never gotten along with my wireless card.

But I'm at a point now where I think I will upgrade to Hardy because too much about Dapper is out of date (and I can't install Firefox 3... actually, I did anyway, and now it seems to be broken :oops: ).

I currently dual boot Kubuntu/WinXP (WinXP is just for Ventrilo and Fraps) and I'm curious to know if sticking the Hardy CD in my computer and reinstalling Linux from scratch is going to touch my Windows partition or if I need to do anything special when installing to keep it intact.

Thanks in advance!

---

### Post by avtolle on 2008-06-18
Well, insofar as the installation is concerned, so long as you know which partition(s) on your HDD are occupied by your Windows installation, and you don't touch them during the partitioning stage, you should be OK. Manual partitioning is likely the best. One thought: before beginning the installation process, you could delete your Kubuntu partitions, and then during the installation, select the guided partitioning - use largest available space (or something close to that). Again, so long as you don't mess with the XP partition(s), you should not lose Windows.

EDIT: Forgot the two things that are perhaps the most important: 1) Back up your data; 2) Do NOT select the option under guided partitioning to "use entire disk".

---

### Post by Pikestaff on 2008-06-19
> **avtolle said:**
> Well, insofar as the installation is concerned, so long as you know which partition(s) on your HDD are occupied by your Windows installation, and you don't touch them during the partitioning stage, you should be OK. Manual partitioning is likely the best. One thought: before beginning the installation process, you could delete your Kubuntu partitions, and then during the installation, select the guided partitioning - use largest available space (or something close to that). Again, so long as you don't mess with the XP partition(s), you should not lose Windows.

EDIT: Forgot the two things that are perhaps the most important: 1) Back up your data; 2) Do NOT select the option under guided partitioning to "use entire disk".

That worked very nicely, thank you, although I still ended up messing things up due to my own panicking =P  Because Grub was freaking out and giving me errors afterwards so I wiped the entire drive (including Windows) instead of just fixing Grub, and reinstalled... but regardless, what you said did work, I just didn't know it at the time! =P

---

