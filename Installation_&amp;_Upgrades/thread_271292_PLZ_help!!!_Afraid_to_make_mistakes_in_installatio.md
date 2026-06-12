---
title: "PLZ help!!! Afraid to make mistakes in installation"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by afzalnaj on 2006-10-04
hey, plz help me with this stuff:

I got the cds of Ubuntu today so i booted from the cd. I tried Ubuntu then decided to install it.
When i reached the Partition Step (Step 5), i was confused . I selected manually edit partition table.

   1. I want to install Ubuntu on the last partition (sda7) it is 20GB Fat32, is this fine for the installation?
   2. I can resize that partition so that i can get 500 MB for swap partition, but what i want to know is how do i select it to be a swap partition (do i select "linux-swap" in the filesystem dropdown)?
   3. Why is it showing the first partition (sda1) as the a boot lba (and what does boot lba mean?), would it affect my Win XP installation?
   4. Ok, then i move on to the next step.
      Where every partition is set as "/media/sda#"
      should i change "/media/sda7" to "/"?
   5. When selecting the swap partition in the same step as above, should i select the swap partition as "/swap"?

---

### Post by whizbaby on 2006-10-04
> **afzalnaj said:**
>    1. I want to install Ubuntu on the last partition (sda7) it is 20GB Fat32, is this fine for the installation?
Not quite. You can delete it and partition the free space ():
((swap)(rest))
with swap size approx two times your physical RAM (1Gig RAM ~ 2Gig swap space) and linux-swap filesystem as you thought, the rest as ext3
> 
      4. Ok, then i move on to the next step.
      Where every partition is set as "/media/sda#"
      should i change "/media/sda7" to "/"?
   5. When selecting the swap partition in the same step as above, should i select the swap partition as "/swap"?
Yes, good idea.
EDIT:
Oh, and check that only partitions you want to are formatted (checkbox).

---

### Post by az on 2006-10-04
> **afzalnaj said:**
> 

   1. I want to install Ubuntu on the last partition (sda7) it is 20GB Fat32, is this fine for the installation?
   2. I can resize that partition so that i can get 500 MB for swap partition, but what i want to know is how do i select it to be a swap partition (do i select "linux-swap" in the filesystem dropdown)?
   3. Why is it showing the first partition (sda1) as the a boot lba (and what does boot lba mean?), would it affect my Win XP installation?
   4. Ok, then i move on to the next step.
      Where every partition is set as "/media/sda#"
      should i change "/media/sda7" to "/"?
   5. When selecting the swap partition in the same step as above, should i select the swap partition as "/swap"?

If you are really concerned, why not take the default option instead of manualy editing the partition table and let the installer create the space by shrinking a partition?

Alternatively, you can make your life easy by going into manual partitioning and then deleting the partition you mention.  You will then have FREE SPACE that the installer can use to create the root and swap partition for you.  You would just have to back up (move backwards) and then select the USE FREE SPACE option instead of manual partitioning.

Otherwise, 
1-  You will need to reformat that to ext3.  The installer will do that for you.  It is fine as it is, it does not have to be changed before you do the install, just do not keep the filesystem on that partition when you use manual partitioning.
2- See 5.
3-  LBA means that older motherboards were not able to see more than 8 gigs of hard drive space.  LBA was a mode that some motherboards started to use when bigger hard drives were around.
4- yes
5- yes

---

### Post by afzalnaj on 2006-10-04
> Not quite. You can delete it and partition the free space ():
((swap)(rest))
with swap size approx two times your physical RAM (1Gig RAM ~ 2Gig swap space) and linux-swap filesystem as you thought, the rest as ext3

with ubuntu installation in (rest)??

Thanx goes to 
azz and whizbaby

and azz i dont wanna go with the default option coz i have to save my winxp os too

---

### Post by az on 2006-10-04
> **afzalnaj said:**
> with ubuntu installation in (rest)??

Thanx goes to 
azz and whizbaby

and azz i dont wanna go with the default option coz i have to save my winxp os too

Yes, with the Ubuntu installation (the root partition) on the rest.
Also, unless the default option you get is to format the entire disk, you will not lose your other OS.

---

### Post by afzalnaj on 2006-10-04
Do i really need to contest the ubuntu partition to ext3 coz i read that there are probs with ext3 partition on SATA hdds

thanx for all the help im ready to install ubuntu
is there any good web developing software for ubuntu and does ubuntu have an apache server preinstalled?

---

### Post by afzalnaj on 2006-10-04
Man its showing an exclaimation mark on sda1 and saying that do you have the plugins for this filesystem. Its a fat32.
But the installation still continues so now im not afraid to try!

---

### Post by az on 2006-10-04
> **afzalnaj said:**
> Man its showing an exclaimation mark on sda1 and saying that do you have the plugins for this filesystem. Its a fat32.
But the installation still continues so now im not afraid to try!

You cannot install ubuntu on a fat32 partition.   That filesystem does not support unix permissions.

There should be no problem using ext3.  You really need to change the filesystem to ext3 (format the partition and start over)

---

### Post by afzalnaj on 2007-08-12
ok man...i installed the last time! and then i removed it...i ve installed now in the ext3...now i think im getting the hang of this..thanks for the help
now i just need to set up the internet on ubuntu...i lost hope last year n left the forum!! now the ubuntu spirit is back with me!

thnx for the help again

---

