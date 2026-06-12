---
title: "WinXP &amp; 2 Distros minus 1!!"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by OutCell on 2007-06-13
Hi,

I installed Ubuntu 7.04 couple of days ago (From the DVD provided by Linuxformat magazine). I have WinXP & openSUSE 10.2 installed before. Now i thought that Ubuntu's installation would overwrite openSUSE (I think it worked when i overwrote Fedora with SUSE), so now i have WinXP, SUSE and Ubuntu.

How can i delete SUSE and add the free space to Ubuntu? I know i am suppose to use GParted and delete the partitions but i don't know the exact way in doing what i want without screwing anything up! Can someone please give me a link to a step by step tutorial?

I installed Ubuntu 6 before and had troubles with my wireless card, but Ubuntu 7 is way better than i expected and i think i am going to make it my main OS from now on :D

Thanks for your wonderful OS!!! :KS

---

### Post by OutCell on 2007-06-15
Any one able to help out there!!

---

### Post by benson444 on 2007-06-15
Hey there,

If Ubuntu is on the last partition and Suse is between Ubuntu and XP then I'm not sure how to go about this. If you haven't done much setting up and you can easily get back to where you are now then the easiest way would be to delete all the Linux partitions and install Ubuntu again.

That's probably what I'd do, but hopefully someone will come along who knows what they are doing and let you know if there's a better way...

---

### Post by OutCell on 2007-06-15
> **benson444 said:**
> Hey there,

If Ubuntu is on the last partition and Suse is between Ubuntu and XP then I'm not sure how to go about this. If you haven't done much setting up and you can easily get back to where you are now then the easiest way would be to delete all the Linux partitions and install Ubuntu again.

That's probably what I'd do, but hopefully someone will come along who knows what they are doing and let you know if there's a better way...

First of all thanks for your reply :)

Well i didn't do much except install some software and changed the appearance of the Desktop.. I thought of deleting all linux partitions and installing Ubuntu again but i thought why not just wait and see if there is a way to fix this without deleting Ubuntu. I guess i will do that anyways now because i kind of change settings by the day and don't want to forget something i changed :D

Thanks again (Going to delete now lol)

---

### Post by OutCell on 2007-06-15
Ok i was able to delete SUSE's partition but i couldn't resize Ubuntu's partition. The resize/move icon is shaded :( and there is a lock icon on Ubuntu's partition (sda4). This is a picture:

[IMG]http://i169.photobucket.com/albums/u233/OutCell/Screenshot.png[/IMG]

Can i add the free space to Ubuntu (~33gb) without deleting and installing Ubuntu again?

Thanks

---

### Post by benson444 on 2007-06-16
I believe you can't resize the partition because it's mounted. Either use the Ubuntu desktop CD, if you have the desktop one, or download a copy of GParted Live CD

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Then you can resize sda4 to use up all the unallocated space.

Edit: Just noticed you don't have a swap. Didn't look properly and thought the fat32 was swap. So, anyway, you'll obviously want to add one.

---

### Post by OutCell on 2007-06-16
> **benson444 said:**
> I believe you can't resize the partition because it's mounted. Either use the Ubuntu desktop CD, if you have the desktop one, or download a copy of GParted Live CD

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Then you can resize sda4 to use up all the unallocated space.

Edit: Just noticed you don't have a swap. Didn't look properly and thought the fat32 was swap. So, anyway, you'll obviously want to add one.

Thanks Benson.. I will get the LiveCD and do it from there :D

I am getting errors when i try to update Ubuntu ever since i delete the swap (Thinking it was SUSE's)..

---

### Post by Pumalite on 2007-06-16
> **OutCell said:**
> Thanks Benson.. I will get the LiveCD and do it from there :D

I am getting errors when i try to update Ubuntu ever since i delete the swap (Thinking it was SUSE's)..

Give about 10GB to'/', one and a half to twice the amount of your memory to 'swap' and the rest to 'home'.

---

### Post by OutCell on 2007-06-16
> **Pumalite said:**
> Give about 10GB to'/', one and a half to twice the amount of your memory to 'swap' and the rest to 'home'.

Thanks Pumalite. I gave 4GB to swap as i have around 2GB RAM (Choose primary but i feel that i am suppose to choose extended). But how do i know which is "/" and which is "/home" on the Ubuntu partition (sda4)? I just resized the partition from around 10GB to around 30GB .. And 10gb left added to the fat32 partition.

---

### Post by benson444 on 2007-06-16
> **OutCell said:**
> Thanks Pumalite. I gave 4GB to swap as i have around 2GB RAM (Choose primary but i feel that i am suppose to choose extended). But how do i know which is "/" and which is "/home" on the Ubuntu partition (sda4)? I just resized the partition from around 10GB to around 30GB .. And 10gb left added to the fat32 partition.

So you now have 4 partitions? 26Gig for XP, 30 for Ubuntu, 4 for swap and 14 for fat32?

"/"  and  "/home" are directories that are both on sda4. You can put /home and others on separate partitions if you want. There are guides to do this after you've installed. I haven't done it yet, always just creating / and swap.

Edit: Just searched and found this link [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by OutCell on 2007-06-16
> **benson444 said:**
> So you now have 4 partitions? 26Gig for XP, 30 for Ubuntu, 4 for swap and 14 for fat32?

"/"  and  "/home" are directories that are both on sda4. You can put /home and others on separate partitions if you want. There are guides to do this after you've installed. I haven't done it yet, always just creating / and swap.

Edit: Just searched and found this link [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Yes i have 4 now. Is this ok? 

26gb                                   /dev/sda1 -- ntfs
30gb                                   /dev/sda4 -- ext3
4gb                                     /dev/sda3 -- linux-swap
14gb                                   /dev/sda2 -- fat32

---

### Post by benson444 on 2007-06-16
Yeah, man. With the amount of RAM you have you could make swap smaller, say 1-2 Gigs, freeing up more for Ubuntu on sda4 if needed (I should have said that before...) but yep, looks good to me.

---

### Post by OutCell on 2007-06-16
> **benson444 said:**
> Yeah, man. With the amount of RAM you have you could make swap smaller, say 1-2 Gigs, freeing up more for Ubuntu on sda4 if needed (I should have said that before...) but yep, looks good to me.

Thanks Ben :)

---

