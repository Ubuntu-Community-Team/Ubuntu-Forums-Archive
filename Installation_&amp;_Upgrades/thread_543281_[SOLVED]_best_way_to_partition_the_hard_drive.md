---
title: "[SOLVED] best way to partition the hard drive?"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by shortybookit on 2007-09-04
i am burning the iso file right now after i make sure it works

i am going to partion

what is the best way to do it  to dual boot with XP?

partion 1 is going to be XP---NSTF
partiton 2 is going to be ubuntu linux
partition 3 is going to be swap

what is th ebest format for the ubuntu linux? nstf? or fat32?

---

### Post by wolfen69 on 2007-09-04
ubuntu doesnt use ntfs or fat32. it is usually ext2/ext3/reiserFS. see this [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Pumalite on 2007-09-04
ext3

---

### Post by shortybookit on 2007-09-04
if i have a 75gb HD how would you recomend breaking it up 
would 50 gb for xp 24 gb for linux and 1gb swap?

---

### Post by Pumalite on 2007-09-04
500 MB swap
10 GB '/'
Rest for /home

---

### Post by shortybookit on 2007-09-04
so if iwant to install xp as well on a 75gb hard drive i would do 
partition one xp--nstf---------------------------------------------------------------------------50gb
partiton 2 linux ubunta ext3 woulb be the / i am assuming?-------------------------------10gb
partiton3 swap-linux swap----------------------------------------------------------------------500mb
partition 4 /home?--what format ext3? would this be for files i would write and read?--15gb

---

### Post by Pumalite on 2007-09-04
You don't have to assign an exact amount to /home; you can just leave the 'rest' to /home.( I like ext3 but you can choose whatever you like except ntfs or fat32)

---

### Post by shortybookit on 2007-09-04
ok-- is /home for files i download and create that is were i would save them am i assuming right?
the / is again an assumption were the system files go for ubuntu and nothing more?

---

### Post by Pumalite on 2007-09-04
Programs you install also save their conf files in home (.xxx; hidden files)

---

