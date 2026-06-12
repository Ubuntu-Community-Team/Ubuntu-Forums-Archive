---
title: "KUbuntu + XP"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by Quando on 2006-09-10
Hi, I downloaded Kubuntu and I want to install it along with my windows XP (I'm still new to Linux and want to get used to it with having the alternative I'm used to if I run into problems...)

Anyway, the live thing works great... I want to install it on my harddrive.

I have one partition (about 74GB) which WinXP and all the rest of my stuff also sit on.

I tried installing but then I get some messages there and I'm afraid that if I will do something 'wrong' it will delete my WinXP and the rest of my things.

Can you give me some advice on what I should do? I'm really new to this.

---

### Post by orb9220 on 2006-09-10
Well first you must defrag the hell out of the xp partition.
Then during the install you must select manually partition.

Then you must have enough free space so that you can resize or shrink the partition down and have about 10-15GB free that ubuntu can use.
You will be creating a root account which is denoted by  /  and a linux-swap space which is usally twice the size of your ram.

So a 15GB of unallocated space freed by resizing your xp partion would allow you to creats a 14GB /  and 1gb linux-swap space.

---

### Post by Quando on 2006-09-10
Hi, thanks for your help :)
This is where I'm at now:

[http://img182.imageshack.us/img182/4435/snapshot1gm6.png](http://img182.imageshack.us/img182/4435/snapshot1gm6.png)

What should I do next?

Thanks :)

---

### Post by Quando on 2006-09-10
Hi, thanks for your help :)
This is where I'm at now:

[http://img182.imageshack.us/img182/4435/snapshot1gm6.png](http://img182.imageshack.us/img182/4435/snapshot1gm6.png)

What should I do next?

Thanks :)

---

### Post by orb9220 on 2006-09-10
install to sda1 which is the free space for the linux.

---

### Post by deleted1028 on 2006-09-10
Hey, you shouldn't have any big problems, I installed Ubuntu on my brothers notebook which had xp, But had to resize the partitions because he didn't have any free space. Nothing got damaged. But since you already have free space just use the guided partitioning on the free space and there shouldn't be a problem. You should end up with the xp stuff and a root, swap, and boot partion for kubuntu.Before I installed Ubuntu on my new computer installed alot of different versions of linux on a test computer before I gave it away. I never ran into any major problems. Having tried both the live and alternate cd's, the alternate cd's were faster for me.On my own computer I have OsX and Ubuntu, but originally had osX and Kubuntu. --scott

---

