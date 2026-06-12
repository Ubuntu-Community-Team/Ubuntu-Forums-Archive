---
title: "Very Confused installing dual boot with XP"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by TheDieSeL on 2010-08-07
I'm still new to ubuntu and been installing it for about a month  and it seems that i'm doing it wrong according to my friends ....

My Drivers are like this :

C: 32 GB  (XP installed)
D: 127 GB Multimedia
E: 97 GB Games
F: 54 GB Various Data

10 GB Unpartitioned Space 

-----------------
What i choses  is install beside windows and created this :

9 GB ext4   mount point :   /boot
1.8 GB SWAP

And i marked the 9 GB  ext4 drive for format 
---------------------------------
What i wanted to do  is to install ubuntu ALONE on that 9 GB Drive  But i don't think that this what happened  Because the last time i formated my C Drive  the boot only showed XP and i re-installed ubuntu on the same setup...
---------------------------


What i'm doing wrong ?? 

What's the best recommended way to install ubuntu for me ? 

and lastly :  What is the Optimum Space i should use  ?? is the 10 GB Enough and Do i need the 1.8 GB  Swap ??

-----------------

Sorry for this long post

---

### Post by oldfred on 2010-08-07
9GB is not generous but it will work. Especially since you have most of you data currently in other partitions. I have lots of programs in my 25GB root partition and have used about 6GB, but you may need 4GB of temp space to write a DVD, so I generally recommend 10-20GB for root. My home is separate and about another 1GB and all my data is in a /data partition.

Swap can be 2GB or the size you have created. You only need it to be the same as RAM if you want to hibernate. After you have run Ubuntu a while and decide you like it, I think you will want more space, but it will work for now.

To see where everything currently is installed from the liveCD download and run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste the contents of results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by TheDieSeL on 2010-08-07
So Next time i think i'm going to shrink the last drive for getting 20GB for ubuntu ,,,, BUT STILL you didn't reply to the main Question ,, Am i doing it WRONG ?? Was the setup settings  Right ?? did i installed on C Drive or what ?

And Thanks for your information and your care I Really Appreciate it

---

### Post by kansasnoob on 2010-08-07
> **TheDieSeL said:**
> I'm still new to ubuntu and been installing it for about a month  and it seems that i'm doing it wrong according to my friends ....

My Drivers are like this :

C: 32 GB  (XP installed)
D: 127 GB Multimedia
E: 97 GB Games
F: 54 GB Various Data

10 GB Unpartitioned Space 

-----------------
What i choses  is install beside windows and created this :

9 GB ext4   mount point :   /boot
1.8 GB SWAP

And i marked the 9 GB  ext4 drive for format 
---------------------------------
What i wanted to do  is to install ubuntu ALONE on that 9 GB Drive  But i don't think that this what happened  Because the last time i formated my C Drive  the boot only showed XP and i re-installed ubuntu on the same setup...
---------------------------


What i'm doing wrong ?? 

What's the best recommended way to install ubuntu for me ? 

and lastly :  What is the Optimum Space i should use  ?? is the 10 GB Enough and Do i need the 1.8 GB  Swap ??

-----------------

Sorry for this long post

This:

> 9 GB ext4   mount point :   /boot
1.8 GB SWAP

Is wrong!

A "/boot" is only a boot partition!

If you're trying to create only a root partition and SWAP the you should choose "/" instead of "/boot" :D

---

### Post by TheDieSeL on 2010-08-08
i want to have ubuntu fully functional from the 9 GB ext4 Drive and don't want it to store any system components on C Drive .... What should i do ??

9GB ext4 mount point /
1.8GB SWAP

Or what ??

---

### Post by TheDieSeL on 2010-08-11
> **TheDieSeL said:**
> i want to have ubuntu fully functional from the 9 GB ext4 Drive and don't want it to store any system components on C Drive .... What should i do ??

9GB ext4 mount point /
1.8GB SWAP

Or what ??
Is this the Right setup ?? Please i'm reinstalling tomorrow

---

### Post by oldfred on 2010-08-11
Are all your partitions primary? If so you have used all 4 primary partitions and cannot add any more. One primary can be an extended that can hold many more logical partitions. If you have used all primary partitions, you will have to back up and then delete one partition. You can  then make the space the extended partition and put in the data you saved and the new partitions you want.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

