---
title: "how to format Win XP sitting on different drive than Ubuntu"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by kkirtac on 2008-07-07
Hi, i have Ubuntu 8.04 installed in the D drive of my system and Win xp sits on the C drive. I just wanted to format my XP and install a new one to C drive. I inserted the win xp cd and it asked me to boot from cd, i said yes and it always showed black screen with no operation after then...what should i do ?

---

### Post by VMC on 2008-07-07
> **kkirtac said:**
> Hi, i have Ubuntu 8.04 installed in the D drive of my system and Win xp sits on the C drive. I just wanted to format my XP and install a new one to C drive. I inserted the win xp cd and it asked me to boot from cd, i said yes and it always showed black screen with no operation after then...what should i do ?

Are those separate hard drives or  partitions?

Also, once you install XP again you are going to have to re-install Grub as well.

Are you sure the Windows XP disk is a install disk.

---

### Post by kkirtac on 2008-07-07
xp is on a different drive than ubuntu but they are on the same disk..hmm yes different partitions..what do you mean by install disk and why do i have to install ubuntu again..they are on different partitions

---

### Post by zvacet on 2008-07-07
> what do you mean by install disk and why do i have to install ubuntu again..they are on different partitions

It mean that disc is bootable,so you can install from it.You don´t have to reinstall Ubuntu,just **grub**.[Here.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by kkirtac on 2008-07-07
yes i m sure that its a bootable CD :S

---

### Post by kkirtac on 2008-07-08
hmm..any suggestions about formatting the C partition in this situation ?

---

### Post by VMC on 2008-07-08
> **kkirtac said:**
> hmm..any suggestions about formatting the C partition in this situation ?

Going back to your first question, "I inserted the win xp cd and it asked me to boot from cd, i said yes and it always showed black screen with no operation after then...what should i do ?"

Something is wrong with that XP install disk or maybe something in your BIOS setup. Once you insert your XP install disk it should start the process of booting up and detecting your hard drives.

---

