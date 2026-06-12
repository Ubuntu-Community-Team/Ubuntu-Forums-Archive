---
title: "reinstalling Ubuntu"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by generollins on 2008-09-05
Hi peeps!!

I have several installations of Ubuntu and several partitions. I want install a fresh copy and have got stuck.

I have deleted all the old partitions so now I have

hda1: 5GB (Acer recovery partition)
hda2: 55GB (C Drive)
hda3: 30GB (D Drive)
hda4: 28GB free

I want to install Ubuntu on the hda4 but am not sure what I'm supposed to partition. I did have Compiz fusion working on an earlier installation but it kept complaining about running out of disk space and then it stopped working.

Can someone just guide me as to what I need to do? I basically want asy 25GB for disk space with linux then was going to leave 1GB for the GRUB loader. Then I get stuck with what a Swap partition is and what the "/" is etc

---

### Post by Herman on 2008-09-05
> I have several installations of Ubuntu and several partitions. I want install a fresh copy and have got stuck.
I have deleted all the old partitions so now I have
hda1: 5GB (Acer recovery partition)
hda2: 55GB (C Drive)
hda3: 30GB (D Drive)
hda4: 28GB free
I want to install Ubuntu on the hda4 but am not sure what I'm supposed to partition.Is hda4 an 'extended' partition? You can make more partitions inside an 'extended' partition, so I hope it is.
We can only have up to four 'primary' partitions.
> Can someone just guide me as to what I need to do? I basically want asy 25GB for disk space with linux then was going to leave 1GB for the GRUB loader. Then I get stuck with what a Swap partition is and what the "/" is etc
You could just make a small logical partition for GRUB there first, I don't know why you want a whole GB, but that's up to you, do as you like. Probably 100 MB would be way more than enough. [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").
Then, all you need to do is boot your Ubuntu Desktop Live/Install CD and select the free space and choose 'guided partitioning, it should go something like (but not exactly) like in this link: [COLOR=#000000][Hardy Heron LTS / Windows XP Dual Boot Installation A]("http://www.herman.linuxmaniac.net/p24.html")[/COLOR]

The slash: / is shorthand for the 'root' file system, which generally means the main operating system partition, something like the equivalent of your 'C drive' in Windows language. 
Your 'swap area' (or partition), acts like a 'page file' in Windows, it's an area of the hard disk for temporarily storing files that need to intermittently accessed by the operating system. It's mainly used when there isn't enough RAM, it becomes very important in computers with less than say around 380 MB of RAM. You probably only need a small swap area, these days most computers have 512 MB of RAM or 1 GB or more. The installer can create one for your automatically. I normally make my swap area 1 GB if I do it myself, but that's way too big really.
The easiest (and best) thing to do is just use 'guided partitioning', and let the Ubuntu installer do it all for you.

---

### Post by Elfy on 2008-09-05
Never heard of needing 1Gb for the GRUB loader.

You will need to make an extended partition in the empty space. Inside that create logical partitions, 1 for swap - and 1 or 2 ext3 depending...

/ is root and all of the install will be inside it, unless you decide on a seperate /home, swap needs to be seperate.

If you have no need for hibernation then swap could be as little as 512BM if RAM is greater than 1Gb, if RAM is less than 1Gb then swap = 1.5xRAM.

The remainder can then be for / - I used to have seperate /home but now prefer to keep data seperate.

---

### Post by generollins on 2008-09-06
sorry i know the GRUB loader only uses about 100MB or so but wasn't sure what the minimum size was.

Anyway I've installed it as i grew impatient waiting last night!!! I have a swap partition of 1GB and the "/" partition set to 26GB

Just setting up so I can use the fancy bits like cube etc!

---

### Post by Herman on 2008-09-06
> Anyway I've installed it as i grew impatient waiting last night!!! I have a swap partition of 1GB and the "/" partition set to 26GB
Just setting up so I can use the fancy bits like cube etc!:) Cool!
> sorry i know the GRUB loader only uses about 100MB or so but wasn't sure what the minimum size was. Well I suppose it doesn't hurt to err on the safe side, now that it's so easy to mount/unmount partitions these days, (with Hardy Heron), it would be easy to put some extra files in there if you wanted to hide them or if you needed to utilize all of your disc space. :)

---

