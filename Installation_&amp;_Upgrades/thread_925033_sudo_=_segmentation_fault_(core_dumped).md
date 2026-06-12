---
title: "sudo = segmentation fault (core dumped)"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by rwabel on 2008-09-20
I've done some bad libc6 upgrades and since then all su or sudo commands terminate with a segmentation fault

I've tried to follow **[howto : repair your broken ubuntu using livecd]("http://ubuntuforums.org/showthread.php?t=422523")**, bit that also doesn't help as I get ther the same error

ubuntu@ubuntu:/etc$ sudo chroot /mnt/repair su
Segmentation fault (core dumped)
ubuntu@ubuntu:/etc$ 

Is there a way to still be able to fix my system?

---

### Post by Pumalite on 2008-09-20
Post the entire output of:
sudo --configure -a

---

### Post by rwabel on 2008-09-20
> **Pumalite said:**
> Post the entire output of:
sudo --configure -a

I can even no longer log into my system

---

### Post by rwabel on 2008-09-20
or is there a way to upgrade the system to ibex for example without needed to log into the current system? This would for sure fix the issue

---

### Post by Pumalite on 2008-09-20
Can you get into Recovery Mode?

---

### Post by rwabel on 2008-09-20
> **Pumalite said:**
> Can you get into Recovery Mode?

no oit also segment faults after a while

---

### Post by Pumalite on 2008-09-20
Save your data and do a clean install. Check your drive with TestDisk while you are at it.

---

### Post by rwabel on 2008-09-20
> **Pumalite said:**
> Save your data and do a clean install. Check your drive with TestDisk while you are at it.

the drive is not the problem, the only problem is that I did upgrade wrong libc6 package. I would like to keep the current installation and just fix libc6, but it seems impossible due to that segmentation fault, as not able to boot into the OS, from rescue I also get that segmentation fault.

probably I really need to install my os new. I will then go directyl with ibex and manually put back the important stuff from my old hardy parition

---

### Post by rwabel on 2008-09-20
Did a new installation and all fine now. At least I have now after several generations of upgrade a new clean installation

---

