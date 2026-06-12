---
title: "confusion after installation ubuntu! did i do it right??"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by neo1691 on 2011-06-26
[SIZE=2][SIZE=3][COLOR=Red]**PAST**[/COLOR][/SIZE]

I had installed ubuntu 10.10 long back[/SIZE] [SIZE=2]but never really used it much due to academical commitments. I had installed ubuntu on a separate partition of 20 gb. I dont remember exactly what all values i had selected for various partition and i was very much confused while installation!! I somehow managed to install it and this is what i got while booting my laptop!

[IMG]http://dl.dropbox.com/u/25234323/boot.JPG[/IMG]

Apart from that my home and desktop size were very less. I remembered myself giving 6 gb to swap (as i considered swap to be important).

here is what i get when i mount type in terminal!!
[IMG]http://dl.dropbox.com/u/25234323/ubuntu%20mount.png[/IMG]

[B][SIZE=3][COLOR=Red]Present[/COLOR][/SIZE][SIZE=3][COLOR=Red]
[/COLOR][/SIZE][/B][SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
I have downloaded the new ubuntu 11.04 and i want to start over again by totally formatting my 20 gb hardisk that i created!! Also i want to keep at least 30 gb for my new drive!!

can anyone advice me what sizes exactly should i used for this installation for various file systems!! Thanks!!
[/COLOR][/SIZE][/COLOR][/SIZE][Here ]("http://www.gadgetsguru.in/hp-pavilion-dv6-1111au-notebook-vb627pa-price-specification-buy-india-8169.aspx")are the specs of my laptop!! 
[/SIZE]

---

### Post by oldfred on 2011-06-27
You can just reinstall to your current partitions if you do not want to reformat.

I do not recommend a separate /boot unless you have a old system that only boots from the first 137GB and even then you can have all of / (root) inside the first 137GB in most cases.

Are you still dual booting with windows. If so I also recommend a shared NTFS data partition for any data you want in both.

Otherwise your current setup seems fine.

Even my own 'best' partitioning plan gets old & obsolete after a couple of years. It depends on what you want to do.


For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by neo1691 on 2011-06-28
> **oldfred said:**
> You can just reinstall to your current partitions if you do not want to reformat.

I do not recommend a separate /boot unless you have a old system that only boots from the first 137GB and even then you can have all of / (root) inside the first 137GB in most cases.

Are you still dual booting with windows. If so I also recommend a shared NTFS data partition for any data you want in both.

Otherwise your current setup seems fine.

Even my own 'best' partitioning plan gets old & obsolete after a couple of years. It depends on what you want to do.


For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
thanks a lot for the reply!!! i had already made a 20 gb partition before installing ubuntu 10.10. but i messed up giving stupid value to partitions!!
Now i plan to make a 10 gb extra partition in windows so that i get 10 gb free space while installing ubuntu 11.04.
from your reply i figure out that i have to give max space to the /root partition and then more for /swap partiton!! Other are 2 gb for /home and 2 gb swap..!! 

ALL THE REMAINING GO TO /ROOT!!

can u please elaborate how can i use the ntfs partition if i make an extra 5 gb partition!! And any way i can removing dual booting.. is it required.. for a fast laptop like HP dv6

---

### Post by oldfred on 2011-06-28
How large is hard drive? I made my shared about 20GB and that has worked, but I already was trying to convert from XP to Ubuntu. I have Firefox & Thunderbird profiles & photos in the NTFS partition. 

Now most of my data goes into a /mnt/data partition and I keep /home inside / (root) as /home only has my user settings. I even move some data that is normally in hidden folders into my data partition. 

Do not use windows to create partitions, just to shrink windows. Win7 has a nasty habit of converting to dynamic partitions that are not compatible with anything if you create more than 4 partitions. And it has sometimes changed partition table incorrectly (not sure if win7's or third party windows partitioner).

---

### Post by neo1691 on 2011-06-28
> **oldfred said:**
> How large is hard drive? I made my shared about 20GB and that has worked, but I already was trying to convert from XP to Ubuntu. I have Firefox & Thunderbird profiles & photos in the NTFS partition. 

Now most of my data goes into a /mnt/data partition and I keep /home inside / (root) as /home only has my user settings. I even move some data that is normally in hidden folders into my data partition. 

Do not use windows to create partitions, just to shrink windows. Win7 has a nasty habit of converting to dynamic partitions that are not compatible with anything if you create more than 4 partitions. And it has sometimes changed partition table incorrectly (not sure if win7's or third party windows partitioner).
i am on vista and i use the SHRINK DRIVE option in windows.. Also i will make a partition for sharing files also.. if i can share files without problem!! as it is i jus use my other D drive that i have made to share files.. i simply drop any file from ubuntu in that D drive and open it on windows!! :D

now to get a new installation i will try the following steps..
1. first shrink a drive to more 10-15 gb.
2. boot from ubuntu live
3. select manual installation.
4. reduce swap size to 3 gb
5. increase /root size
6. increase home size

what abt that sda/dev thing..???? anything else i need??

---

### Post by oldfred on 2011-06-28
If you already have a D: drive which is data only not an operating system then that can be your shared partition in Ubuntu, you do not need another. I just do not like writing (reading is ok) into a foreign system no matter how good the reverse engineered driver is.

Not sure what your issue may be with /dev/sda? When you install root is just '/' not /root and for whatever reason swap is just swap.

---

### Post by neo1691 on 2011-06-29
> **oldfred said:**
> If you already have a D: drive which is data only not an operating system then that can be your shared partition in Ubuntu, you do not need another. I just do not like writing (reading is ok) into a foreign system no matter how good the reverse engineered driver is.

Not sure what your issue may be with /dev/sda? When you install root is just '/' not /root and for whatever reason swap is just swap.
okay thanks!! i think i should muster enough courage and go ahead with the installation of ubuntu 11.04

---

