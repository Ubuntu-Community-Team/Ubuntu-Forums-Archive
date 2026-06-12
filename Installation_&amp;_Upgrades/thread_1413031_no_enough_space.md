---
title: "no enough space?"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by BluesWorld on 2010-02-21
I installed with wubi on a new partition with 99GB free space and for some reason when i look at file system i got only 290.7MB free space i check on my vista and it cleary states i have well over 90GB mem still left. btw i only allocated 3GB to wubi as to not use much space for installation. Please help i am looking forward to become depended on Ubuntu based on the high regards of the OS :KS ThAnKs in advance :D

---

### Post by gadolinio on 2010-02-22
Hi. When you install using wubi, the amount of space you choose to give ubuntu at the very beginning (for example 4 GiB) is the maximum space the operative system will have for itself (that is, installed programs, personal documents in your home folder, personal configuration/settings, etc). You can save you photos, documents, music, and other files in the remaining 90 Gib you have left, but anytime you want to instal some application, actualizations, or any other thing more "system-related", let's say, you're limited to those GiB you reserved when you first installed ubuntu.
You can try giving wubi the maximum permitted (I think it's 30 GiB), or install ubuntu in its own partition (that would be the ninety-something GiB one).
I'd try the second option, as ti will give you more potential disk space, and more independency for ubuntu (it will be an actual partition/drive, and not a virtualized operative system).
Feel free to reply if you have any doubts...

---

### Post by BluesWorld on 2010-02-22
I WOULD LOVE THAT SECOND CHOICE! the only questions is how? im not very good at Linux and i don't get it at all

---

### Post by gadolinio on 2010-02-22
OK, let's use that 99 GiB partition. You have to turn the pc on with the live CD, and choose to try ubuntu without making changes to the system. When you start the liveCD session, go to system--> administration--> gparted partition editor. That application will show a graphic representation of your hard disks. You'll see it's quite easy to use, and keep this in mind: before you click the "apply" button, nothing you do will actually be done to your disk. So you can do as many changes as you want, and the only thing that will happen is that you'll see the graphic change, representing what the outcome would be. If you happen to mess things up, just close the program, click the option "don't save changes" or something like that, and the open system--> administration--> gparted partition editor again. This is for you to feel more confident while using the program.
So, back to the process... Select your 99GiB partition, right click it (you can do it in the graphic bar or in the list below it; it's the same) and choose delete. The partition will appear as unassigned. Click apply, and then close gparted. Then in the desktop the liveCD session has an icon for installation; double click it and follow the instructions. When it asks where to install, choose the unassigned space.
If you have any further questions/problems reply back...

---

### Post by viper250 on 2010-02-22
you have a lot of space so you can set up a 40 gib partition for wubi and still have room for more.
asking for help is a wise decision and a good way to make more friend on the forum.
good luck to you

---

