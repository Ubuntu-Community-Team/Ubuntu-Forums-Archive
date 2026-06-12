---
title: "Installing Ubuntu before Vista"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by dc_jt on 2007-10-19
Hi Im having problems installing Ubuntu on my computer which already has Vista installed.

Bascically when I go to install Ubuntu after partitioning my hard drive it doesnt recognise that I have partitioned it, therefore the 'Use the largest continuous free space' option is not there.

I am thinking of formatting my computer and installing Ubuntu first then Vista, any chance this may make a difference?

---

### Post by enchesss on 2007-10-19
Your description is not quite clear enough.

If you have previously partitioned the drive Ubuntu should detect each NTFS or FART partition.

Select the partition you want to use and  - then - you will be given a choice to have Ubuntu to automatically do the swap file.

---

### Post by dc_jt on 2007-10-19
Thats my problem, you say Ubuntu SHOULD detect the partition but it doesnt.

My C drive says Ive got 500gb but apparently ive got 2 x 250gb.

When I boot up computer it says RAID_VOLUME(0) RAIDO(STRIPE)

(Or something like that?)

This mean anything to you?

Thanks

---

### Post by enchesss on 2007-10-19
Again your description is confusing because it is not clear how many drives you have.

If you have partitioned your 500 Gb - how did you do it?

Are they NTFS?

Is it Ubuntu saying that you have RAID enabled or BIOS or Vista?

How many partitions do you want to end up with?

How big is your HD if your C partition is saying 500Gb then how big is the other partition?

It may be better for you to just install a separate HD - It will be well worth the investment to keep things separate and more secure on different formats.

It is a challenge to reinstall grub after you have installed windows over linux so try and do it after.

the new gutsy has a repair grub option but i have not tried it yet even though it will make things easier after you have installed windows over linux.

---

### Post by dc_jt on 2007-10-19
Thanks for the reply.

So if I have a separate hard drive I should have no problem? Just keep Vista no my 500GB one as normal and install Ubuntu on the new hard drive?

How big should the new hard drive be about?

Thanks

---

### Post by kane357 on 2007-10-29
[I]
"Thats my problem, you say Ubuntu SHOULD detect the partition but it doesnt.

My C drive says Ive got 500gb but apparently ive got 2 x 250gb.

When I boot up computer it says RAID_VOLUME(0) RAIDO(STRIPE)

(Or something like that?)

This mean anything to you?

Thanks "[/I]


Your computer is setup on a striped volume, that means it is using two disks as one, it will show as only one disk but in the end you will need to reformat totally because its a dynamic volume ;not a basic volume. Copy your data to a new volume and re install everything and do not change it to a dynamic volume.  ( Striped volumes are good for speed because you have you data split on two hard drive's, and it reads them simultaneously) Do not waste your time trying to keep the volume it wont work. You are already in a dynamic volume ( from my mcsa test I am pretty sure you can not dual boot in that atmosphere)

Install ubuntu and windows on one hard drive with 10-20gb each, and as you need more space create new partitions for each installation. 

You will need to find a usb hard drive or something along those lines , maybe even a dvd/cd burner to offload you data.  I hope someone can find an easier softer way.



I hope that made sense to you, if it did not I will try again : ]

---

### Post by kane357 on 2007-10-29
> **enchesss said:**
> Again your description is confusing because it is not clear how many drives you have.

If you have partitioned your 500 Gb - how did you do it?

Are they NTFS?

Is it Ubuntu saying that you have RAID enabled or BIOS or Vista?

How many partitions do you want to end up with?

How big is your HD if your C partition is saying 500Gb then how big is the other partition?

It may be better for you to just install a separate HD - It will be well worth the investment to keep things separate and more secure on different formats.

It is a challenge to reinstall grub after you have installed windows over linux so try and do it after.

the new gutsy has a repair grub option but i have not tried it yet even though it will make things easier after you have installed windows over linux.

So its better to have ubuntu installed and try to install windows after wards? I am about to install vista on my laptop with an ubuntu install present. Please give me any info you can, i spent allot of time configuring ubuntu to work wiht compiz and the such.

---

### Post by Jose Catre-Vandis on 2007-10-29
It is probably easier to setup the partitions (2 x 20GB then rest for data/share), then install Vista first, and Ubuntu second. This way Ubuntu will pick up Vista along the way and you can boot to both through grub.

I have done it round the other way but it is a bit more of a fiddle.

---

### Post by mrfelker on 2007-10-29
I have invariably found that the easiest way to multiboot is to install MS OS first (and in the order they were developed - XP before Vista for example).  Then install Linux.  You may find it much easier to use the Alternate install CD rather than the desktop CD you seem to be using.  I'd be very surprised if the partitioner (which you run from a text interface doesn't only pickup the Vista parttition but lets you install GRUB on another partition rather than the MS use of the MBR.  Then you will get the very friendly GRUB menu at boot (friendly but not "beautiful").  The alternate install will also let you use the FS of your choice - ReiserFS, JFS etc. I myself use the ReiserFS because I usually have large directories with many small files - which it is suited for.  It's also very fast.  But I am off your topic now.  Try alternate install.

---

### Post by kane357 on 2007-10-29
What a pain, how do i backup my ubuntu settings lol. 

But i have a problem. I tried dual booting a week ago and Vista would not recognize my iso image. Once i deleted vista it was detected, go figure.

---

