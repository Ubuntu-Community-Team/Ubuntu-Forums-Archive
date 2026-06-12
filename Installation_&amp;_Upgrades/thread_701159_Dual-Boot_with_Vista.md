---
title: "Dual-Boot with Vista"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by mlyons16 on 2008-02-19
Hey,

I'm getting ready to install Ubuntu on my desktop. I'm presently running Vista and would like to start using Ubuntu and Vista. 

As for my preparations, I've backed up everything, defragmented my hard drive, and I'm going to go into Computer Management to resize my partitions. I have this info on my C: drive:

1. Total size before shrink in MB: 296198
2. Size of available shrink space in MB: 88487
3. Enter the amount of space to shrink in MB: ?
4. Total size after shrink in MB: (1.-3.)

I'm not sure what value to enter for 3.

---

### Post by the1417 on 2008-02-19
wellcome to linux friend. i am also a newbie, so i will guide you as easy i can. 
1. for the first is preparing you hardisk. you can use fdisk or acronis partition or else.
2. linux want 2 partition to use. one for the instalation and the other swap partition (in windows is virtual memory.
3. the size: for instalation max size i ever use is 20G but i recomend 10 G only (in ext3 partition i recomend), and for swap partition max 2G, but usually is 2 times your RAM size.
4. ok that for preparing HD now for the next step.
5. boot dvd UBUNTU from ROM
6. install ubuntu, there only 7 step.
7. in partition step you can select use bla bla bla (i forgot) or custom partition (i use this option)
8. for linux select the partition has you been prepared you can format again ( ==)) ) and set partition to root ( / )
9. just waiting...
10. reboot and you can enjoy ubuntu.

---

### Post by Pumalite on 2008-02-19
It's better to allocate space for Ubuntu from WITHIN Vista first. (The Vista Partitioner)

---

### Post by mlyons16 on 2008-02-19
So given those figures I posted. What numbers should I populate there?

---

### Post by dstew on 2008-02-19
Give Ubuntu at least 20 gb, and 1 gb for swap. So, total amount to shrink = 21000 MB. Total size after shrink 275198 MB.

---

### Post by mlyons16 on 2008-02-19
> **dstew said:**
> Give Ubuntu at least 20 gb, and 1 gb for swap. So, total amount to shrink = 21000 MB. Total size after shrink 275198 MB.

Alright, thats all I need to do?

When I use the desktop installer from the Ubuntu LiveCD then, what option am I choosing? Use most continuous free space? Or another option?

---

### Post by dstew on 2008-02-19
Use continuous free space. I actually prefer to use the Manual mode so I can see exactly what I am doing. In Manual, you create a root partition out of the unallocated space, 20 Gb in your case, format ext3, mount point /. Then create a swap partition out of the remaining 1 Gb. But that is just me.

My guess is that the Use Largest Continuous Free Space would do the same, but more automatically. My only concern there is what does it mean by "Free Space". I am not sure if it will try to shrink the Vista partition further, since that partition has unused ("free"?) space. I don't know if the installer means unallocated space, or unallocated + unused space in a partition. Maybe others have more experience installing using that mode. I always use Manual.

---

### Post by dabang on 2008-02-19
> what option am I choosing? Use most continuous free space? Or another option?

No, I'd choose "individual" (don't know exactly how it's called, but you'll see) settings, then you'll be presented with a screen showing all partitions. From there you can choose what to do with them,
e.g. format one with ext3 and mount it as "/" and format the second linux partition with swap. Don't touch you Windows partition! ;-) (It'll be mounted automatically.)

---

### Post by dabang on 2008-02-19
dstew was faster ;-) I'd stick to "manual" (yes that's how the option is called)

---

### Post by mlyons16 on 2008-02-19
Haha, okay... I'm gonna try that on my next day off from work, although I'm sure this whole process isn't that lenghty.

I have everything on my external HD (such as my media files), and I do have my HP Recovery CDs on hand in case everything goes to the dogs.

---

