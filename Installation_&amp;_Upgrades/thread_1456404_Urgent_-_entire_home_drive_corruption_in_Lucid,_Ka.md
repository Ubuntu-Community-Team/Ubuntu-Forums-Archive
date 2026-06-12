---
title: "Urgent - entire home drive corruption in Lucid, Karmic dual installation"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by ponkarthik on 2010-04-17
Hi,

I have AMD 64 system with 2 hard drives. I am trying Lucid 64 bit in the first hard drive(sda7 as / and sda8 as /home). Installation goes fine and Lucid runs without errors. The problem starts when boot into my old Ubuntu 9.1 32 bit which is in second drive(/dev/sdb1 as / and /dev/sdb2 as /home) even once. 

After booting into Karmic if I try to boot Lucid it fails with error /home is not present or not ready.

On fdisk or gparted /dev/sda8 is shown as unknown filesystem. fsck.ext4 throws tons of errors. The only way to restore is reinstall or delete the /home partition and reformat to ext4. 

FYI I use encrypted home directory in both versions. 

I have tried this 3 times and it is reproducible every time.

I have not filed a bug yet as I dont know if it is an error with Karmic or lucid.

Please let me know where the error is.

Kind regards
Karthik

---

### Post by mine070 on 2010-04-17
Maybe its because you have a 64 bit pc, and Karmic is 32 bit and Lucid is 64 bit. Shouldn't it be Koala - 64 Bit?

---

### Post by ponkarthik on 2010-04-17
Yes I have 64 bit pc but have been using 32 bit so far as there were issues with flash etc in 64 bit. Now I am trying 64 bit with Lucid.  My win xp 32 bit in /dev/sda works with no problem and the / partition in 64bit is untouched. 

But are they not supposed to co-exist ? I will try again without home encryption.

Many thanks
Karthik

---

