---
title: "Live cd has no issues...but why doesnt it install?"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by lazy_bones1987 on 2008-11-29
Hey everyone, I have been trying to install Ubuntu 8.10 (with little luck)
 My specs are:
Acer Aspire 5710
Intel Centrino Duo 2.0Ghz
1 Gb ram
ATI Radeon HD 2300 (128mb)
140 GB HDD

I'm using Vista as my primary OS (32 bit).

I tried the live cd and everythings working fine...no hardware issues at all...display works fine (I could even enable the special effects) and even the internet works fine. 

So i installed ubuntu using wubi...did a reboot and loaded ubuntu...it installs 100 % and then just hangs....I get a black screen with a cursor blinking....

I researched about it and some ppl say that it might be coz of my hardware and ati drivers....but the live cd worked fine! 

I tried re-installing but i have the same problem....can anyone tell me a way to fix this problem?

---

### Post by icanfly0307 on 2008-11-29
Wubi and the LiveCD are totally different. The LiveCD only shows you what Ubuntu will be like when it's been installed on a *dedicated* partition. However, Wubi gets Ubuntu installed on *Windows* so they're not the same. Even if the LiveCD works, Wubi might or, in your case, might not work.

Just out of curiosity, why did you wan't to go with Wubi? Since the LiveCD works great, I would recommend that you install Ubuntu normally onto a dedicated partition.

Cheers! :)

---

### Post by lazy_bones1987 on 2008-11-29
> **icanfly0307 said:**
> Wubi and the LiveCD are totally different. The LiveCD only shows you what Ubuntu will be like when it's been installed on a *dedicated* partition. However, Wubi gets Ubuntu installed on *Windows* so they're not the same. Even if the LiveCD works, Wubi might or, in your case, might not work.

Just out of curiosity, why did you wan't to go with Wubi? Since the LiveCD works great, I would recommend that you install Ubuntu normally onto a dedicated partition.

Cheers! :)

Hey,
Thanx for your reply. I wanted to go with Wubi because i can install and uninstall ubuntu wherever (even on my D drive) and whenever i want safely without messing up my primary OS (I'm a noob when it comes to these stuff so i wanna play it safe :( ) 

I have a question though....if i create a partition and install it from the cd...would you say that i wont get that blinking screen error again?

Also if i do install after creating a partition...and lets say i want to uninstall it later...can i do that safely without harming the mbr?

p.s. you are the first one to reply to my post....i posted this question in various formats loads of time but no one ever replied...:)

---

### Post by icanfly0307 on 2008-11-29
If you install Ubuntu on a seperate partition, no, you will not face the blinking cursor screen again. And yes you will be able to uninstall Ubuntu if you want to but it will be a bit more complicated. Don't worry though. There's tons of tutorials on uninstalling Ubuntu on the internet and if you still need help, you could always come back to these forums. :)

PS. Whichever way you might choose to install Ubuntu, ALWAYS MAKE A BACKUP OF ALL YOUR DATA!!!

---

### Post by lazy_bones1987 on 2008-11-29
> **icanfly0307 said:**
> If you install Ubuntu on a seperate partition, no, you will not face the blinking cursor screen again. And yes you will be able to uninstall Ubuntu if you want to but it will be a bit more complicated. Don't worry though. There's tons of tutorials on uninstalling Ubuntu on the internet and if you still need help, you could always come back to these forums. :)

PS. Whichever way you might choose to install Ubuntu, ALWAYS MAKE A BACKUP OF ALL YOUR DATA!!!

Just one more question....I have always thought that it should be in the same drive as the other OS

So lets say my primary OS is in C; drive, should i create a partition only in c and then install it? Is it possible for me to create a partition in D and then install it there?

---

### Post by icanfly0307 on 2008-11-29
C: is a seperate partition on its own. You cannot create a partition within a partition. I'm assuming that you only have C: in "My Computer" in Windows. If that's the case, we'll have to resize C: and install Ubuntu in the resulting free space.

Post back and I'll tell you how to resize C:.

Cheers! :)

---

### Post by lazy_bones1987 on 2008-11-30
> **icanfly0307 said:**
> C: is a seperate partition on its own. You cannot create a partition within a partition. I'm assuming that you only have C: in "My Computer" in Windows. If that's the case, we'll have to resize C: and install Ubuntu in the resulting free space.

Post back and I'll tell you how to resize C:.

Cheers! :)

Hey...I have two partitions namely C(where the OS is stored) and D. I did a bit of research and found a tutorial where it shows how ubuntu partitions a drive (Guided Free space something)...

So is it possible for me to install in D ?

---

### Post by icanfly0307 on 2008-11-30
Okay, so here's how it goes. You have a C: and D: right? Well, Ubuntu cannot install onto *any* of those partitions. Think of partitions as a slice of the hard drive. Ubuntu needs a place in the hard drive where there *are no partitions*. So since C: and D: are occupying the entire hard drive, you have to resize one of them to get an *unpartitioned* space on the hard drive. You can do this from the LiveCD installer or from Windows if you have a partitioning software.

How much space do you have on C: and D: ?

I misunderstood partitioning the same way that you did when I was a noob. :) It took me six months to figure out what the problem was every time the installer told me,"Could not allocate free space." ](*,)

---

### Post by studentidiot on 2008-11-30
Use the live CD to install it. Ubuntu can automatically resize the Vista partition during setup to make 3 partitions. (The two you already have, and the new partition for Ubuntu.) Just make sure to choose the option when it asks you early during setup. Or you can install over Vista...

Just make sure you backup all your data and have a Vista restore disk! Enjoy and good luck!

---

### Post by lazy_bones1987 on 2008-11-30
> **icanfly0307 said:**
> Okay, so here's how it goes. You have a C: and D: right? Well, Ubuntu cannot install onto *any* of those partitions. Think of partitions as a slice of the hard drive. Ubuntu needs a place in the hard drive where there *are no partitions*. So since C: and D: are occupying the entire hard drive, you have to resize one of them to get an *unpartitioned* space on the hard drive. You can do this from the LiveCD installer or from Windows if you have a partitioning software.

How much space do you have on C: and D: ?

I misunderstood partitioning the same way that you did when I was a noob. :) It took me six months to figure out what the problem was every time the installer told me,"Could not allocate free space." ](*,)

Hey....I have about 40 gigs of free space in my C: and about 60 in my D:

I'm hesitant to create a partition in C: as i would be using a lot of program files in the future.

So If I'm not mistaken, I can use the vista partition maker to partition my D: and install ubuntu there?

I'm sorry if i'm really dumb about this coz...its just that I have been getting mixed reviews about this from various ppl

---

### Post by lazy_bones1987 on 2008-11-30
> **studentidiot said:**
> Use the live CD to install it. Ubuntu can automatically resize the Vista partition during setup to make 3 partitions. (The two you already have, and the new partition for Ubuntu.) Just make sure to choose the option when it asks you early during setup. Or you can install over Vista...

Just make sure you backup all your data and have a Vista restore disk! Enjoy and good luck!

hey...thanx for your reply....the option you are talking about...which one should i go for? the guided free space? or the manual and theres one more option which i dont quite remember

---

### Post by icanfly0307 on 2008-11-30
If you want Vista to have more space, then don't touch C:. What exactly do you keep in D: ? If it's nothing VERY important, then you might as well make a backup of your stuff in D:, delete it, and install Ubuntu in the free space left over. Remember, you can only delete and create Windows partitions from Windows. Don't create any partitions after deleting D:.

I'll check back soon with more specific instructions. :)

---

### Post by lazy_bones1987 on 2008-11-30
> **icanfly0307 said:**
> If you want Vista to have more space, then don't touch C:. What exactly do you keep in D: ? If it's nothing VERY important, then you might as well make a backup of your stuff in D:, delete it, and install Ubuntu in the free space left over. Remember, you can only delete and create Windows partitions from Windows. Don't create any partitions after deleting D:.

I'll check back soon with more specific instructions. :)

well i dont have anything important there in D: ...btw after I delete D: would my C: get the free space or would i have a "hanging" partition (if there is a partition with that name)

---

### Post by studentidiot on 2008-11-30
Manual can be kind of confusing since you need to setup the swap space manually...

I would recommend deleting the D: partition and then [resizing the C: partition in Vista]("http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista") to take up the whole drive. Then run the guided install on the LiveCD. A weird way to do it, I know, but it's easier to mess with the partitioning under Windows.

BTW, did that D: partition come on the PC? If so, it might be a recovery partition...

---

### Post by lazy_bones1987 on 2008-11-30
> **studentidiot said:**
> Manual can be kind of confusing since you need to setup the swap space manually...

BTW, did that D: partition come on the PC? If so, it might be a recovery partition...

Nope it came with the PC...and its not a recovery partition..

---

### Post by icanfly0307 on 2008-11-30
@studentidiot: Why would he want to resize C: ? Deleting D: would free up enough space (60GB).

---

### Post by icanfly0307 on 2008-11-30
Okay, for your scenario, I think this will be the best way to partition. Remember, **BACK UP YOUR DATA ONTO A DISK OTHER THAN YOUR COMPUTER BEFORE ATTEMPTING THIS**. The reason I've put that statement in capital letters is because I've seen people forget to make backups and lose valuable information. Anyway, back to the procedure:

1. When you get to the partitioning screen, click on Guided - Resize xxx Partition and use freed space.

2. Move your slider bar about halfway. This will let you keep your Windows partition and resize it half of what it was before. The other half will be given to Ubuntu.

3. Click forward

4. Complete the remaining steps and you should be done with the installation in about an hour. :)

Let me know what happens. Good Luck!

---

### Post by lazy_bones1987 on 2008-12-01
> **icanfly0307 said:**
> Okay, for your scenario, I think this will be the best way to partition. Remember, **BACK UP YOUR DATA ONTO A DISK OTHER THAN YOUR COMPUTER BEFORE ATTEMPTING THIS**. The reason I've put that statement in capital letters is because I've seen people forget to make backups and lose valuable information. Anyway, back to the procedure:

1. When you get to the partitioning screen, click on Guided - Resize xxx Partition and use freed space.

2. Move your slider bar about halfway. This will let you keep your Windows partition and resize it half of what it was before. The other half will be given to Ubuntu.

3. Click forward

4. Complete the remaining steps and you should be done with the installation in about an hour. :)

Let me know what happens. Good Luck!

Thanx for your help guys....I have my grad project coming up next week so I wont be doing anything till then (unless i give in to my temptation!)

I will let you know once I have finished installing it (successfully......hopefully)

Once again thankx all for your help!

---

