---
title: "The Partioner and RAID 0"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Ish on 2007-02-05
Okay, I got the CD to boot :D but now I am faced with another prediciment.
I used Norton Partion Magic to partion the harddrives and made a linux partion across my RAID 0. While instaling the partioner is detecting the harddrives as two seperate drives... And I'm not sure how to configure them... Help?

---

### Post by Ish on 2007-02-05
It seems this is a common problem with everyone using a RAID array. I've searched the forums and google for a way to do this but really haven't found anything. It seems that it's a bug or something or that I need another kernal that supports RAID 0? Searching the forums it seems this problem is too common to not have a guide somewhere... I'm a n00b and I just need to know what to do and how to do it. Clear and cut, anyone out there know a solution?

---

### Post by Best04 on 2007-02-06
UP! ):P 

Hy to all!

I am an Italian user. 

I ask all excuse if my English is not perfect (i used ALTAVISTA for translate this message :D ) . 

I would have need also of this aid. My situation is similar (2HD 80gb in RAID0), is on already is installed WinXP. 

I have tried with Kubuntu is what it happens to me is similar to the Ish user. I have tried is with the LiveCD that with the alternated ones. 

According to you if I try with version DVD of Kubuntu I resolve, or better to proceed various? 

Thanks to all! ):P

---

### Post by unisol on 2007-02-06
you could try this:If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer.

---

