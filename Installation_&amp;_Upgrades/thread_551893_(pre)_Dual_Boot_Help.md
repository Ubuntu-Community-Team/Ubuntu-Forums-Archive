---
title: "(pre) Dual Boot Help"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by iheartubuntu on 2007-09-15
Couple quick questions...

#1- all the stuff about dual booting I am reading people who already have XP, want to put Ubuntu on without losing their XP data. Id like to do the reverse. I have Ubuntu and would like to attempt to do a partition, then install XP on the second partition. Is it possible? Any tips? How will XP know where to dump itself?

#2- partitioning my drive. Ive read I can partition my drive so I store key elements of Ubuntu on one partition, and the remainder on the other partition, so if I ever have to reinstall Ubuntu, or upgrade Ubuntu, I wont lose my data and programs. Can anyone point me to the right directions on how to do this? 

Thanks!

---

### Post by Pumalite on 2007-09-15
The best is to install XP first. Windows likes to be sda1. Then install Ubuntu and let Grub install itself in MBR. That way you have a menu to boot either OS. In your case, you can resize your Ubuntu partition and install Windows. Windows will install itself in the MBR, but you can then re-install Grub and edit menu.lst to chainload Windows.

---

### Post by Skidpad on 2007-09-15
#1: [Try this]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

#2: [Try this]("http://www.psychocats.net/ubuntu/separatehome")

(Almost bedtime, I'm a man of few words right now)

:)

---

### Post by iheartubuntu on 2007-09-16
skid, many thanks. i was just reading about making a separate /home partition... your link #2! but my eyes are getting tired so im losing concentration.

---

