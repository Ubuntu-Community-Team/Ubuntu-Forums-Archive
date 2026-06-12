---
title: "Install issues. (please help)"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by Ambby on 2007-07-30
I have an evo-610c laptop,512 ram 2 ghz,40 gig HD.

I deleted some files so i now have 2300 megs free,it should be enough to install on,2 gigs for the OS & the rest for swap,but it always tells me its to small,like im not using enough memory or something?


Alright so i put the live cd in & i boot from disk,i have a single hard drive,& my machine is windows xp,when im using ubuntu i click the install icon,then i go through a few options,it then wants me to choose the root of where i will make a partition from,i do so i make it 2 gigs the minimum,becase i want a duel boot setup & im low on space,when i try & format it a box pops up & says to small.



Linux is awsome,& looks so fricken fun & i really wanna run it :(


I just wanna get this working already & i cant understand whats wrong?


Thanks for reading.

---

### Post by PaulFr on 2007-07-30
Could it be that the 2300 mb you have freed is not contiguous, and so the partition editor cannot make use of the free space since it is all jumbled up with your Windows files ?

Can anyone here confirm whether gparted will be able to defragment the Windows disk before attempting to partition the disk ? I suspect not.

I would anyway suggest you try to defragment your disk in Windows XP to try to get all the free space to the end of the Windows XP partition. Hope this helps.

---

### Post by Ambby on 2007-07-30
Hm,mabye a defrag would help,ill give it a shot!

Hope it works.

---

### Post by Ambby on 2007-07-31
Crap,the defrag did nothing,I dont understand.

Does the partition program from the livecd for ubuntu make new partitions off of a single partition that windows is using?

Mabye im not understanding something?

---

### Post by merlinus on 2007-07-31
The ubuntu partitioner can shrink your windows partition to make room for installation.  It will then make partitions in the freed-up space.

-merlin

---

### Post by Ambby on 2007-07-31
forget this RE go down -_-;

---

### Post by Ambby on 2007-07-31
Ok i get the partition program now,i thought that i had to choose 2000 megs from the main harddrive & it would take it out from avalable space & make the partition,now i see i can see that it edits them to make them smaller,so i tried it it would not even do 300 megs smaller,mabye  have to use a different format instead of ntfs? like change it into another format that mabye takes less space,if thats how it works?


Someone help lol

---

### Post by Ambby on 2007-07-31
Ok so i free'd up ALOT of space,& i saw a slider on how much i wanna compact my partition,so i slide it back & hit ok & it goes for abit then it messed up,do i still need more memory? i dont know whats wrong...

Its driving me crazy,ive been up all day & night & now its morning.

---

### Post by PaulFr on 2007-07-31
1. Running the analyze in Windows XP defragmentation should show you visually where your free space is. After freeing a lot of space, can you run analyze to see if the free space is at the end. If not, please run defrag.

2. Next, I hope you have looked at **[https://help.ubuntu.com/7.04/installation-guide/i386/module-details.html#di-partition](https://help.ubuntu.com/7.04/installation-guide/i386/module-details.html#di-partition)** and more details in **[https://help.ubuntu.com/7.04/installation-guide/i386/partition-programs.html#id2562924](https://help.ubuntu.com/7.04/installation-guide/i386/partition-programs.html#id2562924)**.

Could you tell us what error you are getting after you ran the partition editor in your last post ?

---

### Post by merlinus on 2007-07-31
Usually the windows paging file occupies a large chunk of space near the end of the partition.  You can set that to zero, delete temp files, etc., defrag, and reboot.

Write down the size, and you can restore it after installing ubuntu.

-merlin

---

### Post by Ambby on 2007-07-31
Aright so ive cleared alot more space,i have 8.92 GIGS of free space,i defragged it but the free space at the end of the drive still has bits of unmovable files & whatnot,im also wondering when i use the guided install & i have to use the slider,should i slide it all the way to the left or leave a gig free for swap & whatever else?

Or do i leave it on 100%


Its drving me nuts,it should not be this hard to do x_x


Im gonna try one more time,if i get that error screen ill post what it is,i forgot exactly what it said.

---

### Post by Ambby on 2007-08-01
Ok so i tried to install again & this is the messege i get.

[Resize operation failure]

An error occured while writing the changes to the storage device

The resize operation is aborted




I dont know whats wrong,someone help :(

---

### Post by PaulFr on 2007-08-01
I hope you have followed advice of merlinus regarding Windows page file. Also, I had to run defragment multiple times to get my files away from the end.

Secondly, since the problem is with resize only, I would suggest you focus on that operation only. Can you download the GParted LiveCD available at **[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)** and boot from that and try to resize ? If you can resize using that, then the install can take the empty space and configure your Ubuntu appropriately.

That's it from my end - good luck.

---

### Post by Ambby on 2007-08-01
Well im on ubuntu right now,i pretty much made a mistake & lost my entire windows os lol

So i have a large bit of what i had on this laptop on my desktop,so i guess im not to upset,tho some things were lost that i cant get back,whatever.


Thanks for all the help!

---

