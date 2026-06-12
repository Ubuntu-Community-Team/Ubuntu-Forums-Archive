---
title: "partitioning /, /home, and /swap"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by pic2021 on 2008-06-17
*URGENT!

hey guys i need some help big time. i just bought a new hard drive tonight to put xp and ubuntu studio 4.08 on. i am partitioning my hard drive which is a 250 gb one. i need to know how much gb should i put on each partition. i want to also make a partition for xp so i figured i will do 125 for each partition. i am just curious of how much space i should put on my /home, /, and /swap partition. pleaee help me out now!!!!!




    -Pic

---

### Post by PmDematagoda on 2008-06-17
The swap space is usually recommended to be at least double the amount of RAM, but if you don't hibernate and have a lot of memory then a swap space won't be really necessary.

About the /home and / partitions, you probably should have about 10Gb of / and the rest for /home, but if you are going to install a lot of applications then you may want a larger /, that's entirely upto you, but I think the / partition should be atleast 10Gb large.

---

### Post by pic2021 on 2008-06-17
thank you so much man! that was fast! i actually have 2 gb of ram. how much should i put on?

---

### Post by PmDematagoda on 2008-06-17
> **pic2021 said:**
> thank you so much man! that was fast! i actually have 2 gb of ram. how much should i put on?

If you use a lot of memory intensive applications then about 1Gb of swap would be enough, but if you intend to hibernate then you may need 4Gb of swap, if however you don't use a lot of memory intensive applications then about 512Mb of swap would be more than enough.

---

### Post by pic2021 on 2008-06-17
where do i go to set up the /swap? it isnt a partition is it? so if it isnt where is that located?

---

### Post by PmDematagoda on 2008-06-17
> **pic2021 said:**
> where do i go to set up the /swap? it isnt a partition is it? so if it isnt where is that located?

You can set it up in the partition manager in the Ubuntu installer, and no, it is a separate partition.

---

### Post by pic2021 on 2008-06-17
is that the /srv partition? im really sorry im having a hard time with this. i just want it to be right

---

### Post by pic2021 on 2008-06-17
> **pic2021 said:**
> is that the /srv partition? im really sorry im having a hard time with this. i just want it to be right
*correction.


do i just go to enter manually in the mount point and then type in /swap?

---

### Post by PmDematagoda on 2008-06-17
> **pic2021 said:**
> *correction.


do i just go to enter manually in the mount point and then type in /swap?

Yes you choose manual, but no there is no mount point, just put the partition type as swap and that is all.

---

### Post by pic2021 on 2008-06-17
> **PmDematagoda said:**
> Yes you choose manual, but no there is no mount point, just put the partition type as swap and that is all.
alright i think i got this...

for / i put 20 gb.

for /home i put 105 gb.

for /swap i put 5 gb.

sounds good? and now i have the rest left over for xp.

---

### Post by PmDematagoda on 2008-06-17
> **pic2021 said:**
> alright i think i got this...

for / i put 20 gb.

for /home i put 105 gb.

for /swap i put 5 gb.

sounds good? and now i have the rest left over for xp.

If you are happy with that set-up then it's all right, but I think the swap space may be unnecessarily big.

---

### Post by pic2021 on 2008-06-17
> **PmDematagoda said:**
> If you are happy with that set-up then it's all right, but I think the swap space may be unnecessarily big.
haha then i shall put it to 3 gb or 4 gb. sounds better?? again thank you for all your help man

---

### Post by PmDematagoda on 2008-06-17
> **pic2021 said:**
> haha then i shall put it to 3 gb or 4 gb. sounds better?? again thank you for all your help man

From my experience, 3Gb of space is more than enough for normal usage, but for hibernation I think you should use 4Gb to be on the safe side.

---

### Post by pic2021 on 2008-06-17
thank you so much for all your help i finally got through that step and now it is installing. your a life savior. thank you for all your help!

---

### Post by PmDematagoda on 2008-06-17
> **pic2021 said:**
> thank you so much for all your help i finally got through that step and now it is installing. your a life savior. thank you for all your help!

No problems, if you have any more problems, don't hesitate to ask them:).

---

