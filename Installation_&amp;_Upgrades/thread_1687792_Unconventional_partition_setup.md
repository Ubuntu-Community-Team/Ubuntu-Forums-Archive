---
title: "Unconventional partition setup"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by Bucic on 2011-02-14
The image below is pretty much self-explanatory. PArtition sizes are to scale. The pink swap partition is 2.5 GB for example. Exactly 10 times bigger area is 25 GB.

[IMG]http://i17.photobucket.com/albums/b68/Bucic/ubuntuforumsorg/linux_partitions_custom-1.jpg[/IMG]

Does anyone know of any possible culprits regarding such a setup?

Additional questions:
1. Will such a placment of swap partition screw up boot manager or any part of the booting process on non-dualboot machine?
2. Is it possible to execute all the rearrangements as depicted using the procedure described here? [http://landofthefreeish.com/linux/howto-move-home-to-its-own-partition-after-a-linux-install/](http://landofthefreeish.com/linux/howto-move-home-to-its-own-partition-after-a-linux-install/)

---

### Post by oldfred on 2011-02-14
If you have a separate /data partition then I do not recommend a separate /home. A separate /home is just to separate your user data and your user settings. But user settings are tiny and easily backed up.

Your root seems small.

I do not see swap making any difference on most new machine with more than 2GB of memory. One user (Herman) said he did notice a slightly faster boot with some swap as opposed to none. (But he uses a swap file).

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by Bucic on 2011-02-14
Well, I have 600 MB of RAM :D
I'm on it right now. I'll create empty partitions and I'll get rid of them easily if there are some recommendations not to do as I planned to and I will not need them.

I'm glad I hogged my Ubuntu install with TENS of applications and games. Now I know what to expect. To be honest I'm shocked that a system with so many installed apps occupies only 8 GB of my HDD space right now!


After reading the #3 post - dooh!, sure a separate /home is not needed in my case! I will simply save my downloads, music etc. on the data partition. No need to alter the default /home at all. Thanks!

---

### Post by Bucic on 2011-02-16
The answear for the question 1 is NO. Can anyone try to answear the question 2?

---

### Post by oldfred on 2011-02-16
Is not question #2 about moving /home as that is what the link is about? And I thought you decided not to move /home.

---

### Post by Bucic on 2011-02-16
> **oldfred said:**
> Is not question #2 about moving /home as that is what the link is about? And I thought you decided not to move /home.
No, I mean "all rearrangements" in general and the guide is linked only to show how to copy all the files, hardlinks, softlinks etc.

I'm in the middle of moving /var to a separate partition (as an easier case) as per the guide and I have moving /usr/share/games planned next as a harder case. But I would count on someone stopping me if I'm doing something stupid ;)

EDIT:
Before I mounted the partition with backed up /var/ in place of the original /var I compared contents of the two. They don't match!

[IMG]http://i17.photobucket.com/albums/b68/Bucic/ubuntuforumsorg/var_new.png[/IMG]

This is the command I used:
```
/usr/share/games# **find . -depth -print0 | cpio --null --sparse -pvd /media/var_new**
```

Edit:
Oddly there is a match after I tried the same operation. Worrying inconsistency that shows that proper backup verification procedure is a must. **Does anyone know one or better yet - a copy method that will not require verification?**

---

### Post by oldfred on 2011-02-16
I have moved the /boot partition around, but then moved it back.  I pretty much agree with Herman on having all the system folders in one partition unless you are running a server. I do put my data into a separate partition(s) since that can be much larger. My system partition is normally about 6GB when I have moved all the data from /home to the /data partition.

---

### Post by Bucic on 2011-02-17
> **oldfred said:**
> I have moved the /boot partition around, but then moved it back.  I pretty much agree with Herman on having all the system folders in one partition unless you are running a server. I do put my data into a separate partition(s) since that can be much larger. My system partition is normally about 6GB when I have moved all the data from /home to the /data partition.
I agree with him too. The need to have free space reserve on every partition forces you to leave big gaps and it's exactly the opposite to what short stroking is all about.

My current (finished) setup (in order of physical location on the disk):
2 GB swap
9 GB / (5 GB occupied)
4 GB /var
3 GB /usr/share/games (2 GB occupied)
50 GB /media/data (with all Downloads, Music, Documents etc.)

So as you can see I only move 'archive' type data out of the way.



...
[B]Can I get a confirmation that the command
```
/home# *find . -depth -print0 | cpio --null --sparse -pvd /home_new*
```
will copy all of my files giving me a 100% true backup?

If anyone knows a better method please speak up.[/B]
...

---

