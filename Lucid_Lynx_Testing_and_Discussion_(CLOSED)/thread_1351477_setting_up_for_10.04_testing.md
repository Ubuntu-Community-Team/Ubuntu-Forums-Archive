---
title: "setting up for 10.04 testing"
date: 2009-12-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phillw on 2009-12-10
Hi, I've made a new /home partition (still have my backup one) to share with Koala and Lynx.

As I run a LAMP installation, should I do the same for /usr - or is that release level independant ? (my var/www is small and I can copy it over) - It's just I have my MySQL dbases in that area & not sure whether to link them, or do a clean install of LAMP onto 10.04.

Same applies for the likes of mod-security, ossec, etc. Would I be better (And, as I type I'm thinking yes) to just do a dump of my MySQL dbases & import them into the 10.04 area ?

thanks,


Phill.

---

### Post by cariboo on 2009-12-10
If you are doing this on a computer that you are using to get work done, I would suggest a complete separate partition setup just for Lucid. You will run into a lot of problems trying to share partitions.

---

### Post by phillw on 2009-12-10
> **cariboo907 said:**
> If you are doing this on a computer that you are using to get work done, I would suggest a complete separate partition setup just for Lucid. You will run into a lot of problems trying to share partitions.

Thanks for that - I now have a shared ~home partition and also kept my ~oldhome area within the 9.10 partition.

The changing from ext3 to ext4 went very well - For those coming from 8.04 to 10.04, the transferrance from ext3 --> ext4 & Grub legacy --> Grub2 are looking quite painless.

As I run a desktop environment with added LAMP, I'll be putting 10.04 onto it's own little partition in the next couple of days & then pop LAMP on top of it. Then take a copy of my MySQL Dump files over to it.

Are there any issues that I should be aware of - Or am I going to be the one telling you guyz & galz !!

Regards,

Phill.

---

