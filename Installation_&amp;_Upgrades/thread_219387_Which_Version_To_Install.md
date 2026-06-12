---
title: "Which Version To Install"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by grey_beard on 2006-07-19
I am finally fed up with windows but Im not sure which version of Linux based operating system to install. My computer is an AMD 64 3500+ with 2 gig of corsair ram. I have 2x Galaxy geforce 660GT PCI Express cards running as SLi. My dilemma is I like to play the latest 3d Games.
Can someone please make a suggestion

---

### Post by x64Jimbo on 2006-07-19
It won't really matter what distribution you choose, but you would probably be best off going with a 32 bit distro to start with. The reason for this is that Cedega, which is what you will probably need in order to play your games, is a 32 bit program, and requires a bit of hacking around to get working in a 64 bit environment. Save yourself the trouble, and go with a 32 bit operating system for now. In another couple years or so, 64 bit operating systems will be more common, and by that point, you'll have a much broader knowledge of Linux and you'll be able to decide for yourself.

---

### Post by grey_beard on 2006-07-20
Thanks for the info. I have d/loaded UBUNTU and from the live CD it looks fantastic. Im going to install it to another hard drive in my ssystem so I can learn how to use it. I have d/loaded Cedega as a zip file. I unzipped it to a folder but Im not sure how to install it. Is it command line install?

---

### Post by grey_beard on 2006-07-20
well i must have done something wrong. i installed ubuntu to its own drive and when i try to boot from the drive, it gives me a message "error loading file system". any suggestions?

---

### Post by grey_beard on 2006-07-20
well i have got it running. i now need to know how to change my partition size. it has only given me a 2.1GB partition and by the time iv'e downloaded and update my installation, the partition is full. i have a 40GB hard drive

---

### Post by grey_beard on 2006-07-20
well i must say i have just wasted 5 1/2 hours. I absolutely detest windows, but ubuntu is not a program i would recommend to anyone. It cant setup your hard drive partitions properly by default, it installs the updates, then locks you from your system. There is nowhere that i can find where you can ask questions and have them answered instantly, you have to wait till someone can be bothered reading your postings then hope they reply.
I have to say if i can get it to run properly with a little bit of assisstance, i will be more than happy to stay with it, but at this stage im not impressed. windows may have its faults and bill gates may be a rippoff merchant, but at least his program installs and runs easily

---

### Post by K.Mandla on 2006-07-21
> **grey_beard said:**
> There is nowhere that i can find where you can ask questions and have them answered instantly, you have to wait till someone can be bothered reading your postings then hope they reply.
Sorry no one could help you fast enough. If you needed an instant answer, you might have tried the [Ubuntu chat]("http://www.ubuntu.com/community/irc"). Otherwise, we're all at the mercy of our peers and their relative generosity.

> **grey_beard said:**
> I have to say if i can get it to run properly with a little bit of assisstance, i will be more than happy to stay with it, but at this stage im not impressed. 
Then stick around. Someone might have a suggestion.

For example, you might try pre-partitioning the drive with a live CD of GPartEd. With that, you can resize and define partitions of any flavor -- including Windows partitions -- and set them up before you install. Then you might have avoided the problems you seem to be having with the partitioner. There are plenty of ways to skin a cat.

> **grey_beard said:**
> windows may have its faults and bill gates may be a rippoff merchant, but at least his program installs and runs easily
Interesting. The last time I installed Windows XP on my XPS M170 I had ...

[LIST]
[*]No network line
[*]No wireless
[*]No 3D acceleration
[*]No native resolution
[*]No sound
[*]No touchpad
[/LIST]
My point being, there are problems with both OSes, and neither is perfect. Knowing how to work it is what makes one seem "better" than the other.

The next time you try Linux, please try to give it more than 5 1/2 hours. It's worth it.

---

### Post by grey_beard on 2006-07-21
thankyou for your help, im just downloading the program you mentioned and i will try again, i didnt mean to be rude with my comments, guess i just got a little frustrated

---

### Post by Blutack on 2006-07-21
Yep ,the partitioner can be a bit iffy, but its so worth it in the end.  Knoppix also has qtparted (think open source Partition Magic)  boots off a cd and has tonnes of other useful stuff.  The amount of windows boxes I've saved..

---

### Post by Blutack on 2006-07-21
If you are after games I think there is an ubuntu gaming forum near the bottom of the forums list.

---

### Post by K.Mandla on 2006-07-21
> **grey_beard said:**
> thankyou for your help, im just downloading the program you mentioned and i will try again, i didnt mean to be rude with my comments, guess i just got a little frustrated
That's perfectly understandable. No harm done. :)

---

### Post by grey_beard on 2006-07-22
I wish to thank everybody for their help and support. I now have it running on the entire drive. I have learnt a little bit of patience as well. Will now try the suggestion of using cedega to run the games.

---

### Post by x64Jimbo on 2006-07-22
Another solution for those of you that were suggesting that grey_beard download knoppix or GPartEd LiveCDs...
The Ubuntu LiveCDs can do this too! All you need to do is uncomment the universe lines in /etc/apt/sources.list, apt-get update, and apt-get install gparted, qtparted, partimage, etc. As long as you have an internet connection, an Ubuntu LiveCD is a great system rescue disc!

---

### Post by grey_beard on 2006-07-23
Well everything is going fine. I guess I have a lot to learn. I have a problem now where I cant access drives in my system that are partioned NTFS. I understand that eventually I will be able to partition them as FAT file system, but at this stage there are files on those drives I would rather not lose. I tried reading in another thread how to enable NTFS partitions, but at this stage its over my head. Is there somewhere I can get access to literature that is in very laymans term so I may be able to learn some more. I dont want to keep taking peoples time having to answer my basic question.

---

### Post by Sef on 2006-07-23
> I dont want to keep taking peoples time having to answer my basic question.

Please post your questions, no matter how basic.  I have sometimes solved my problems because someone else with the same problem wrote in and was given an answer.

> I understand that eventually I will be able to partition them as FAT file system, but at this stage there are files on those drives I would rather not lose.

I would back up the data, then reformat, then reinstall the data.  You can also make a partition ext2 or ext3.  Windows and Linux can both read and write to them.

---

### Post by x64Jimbo on 2006-07-24
To write to ext2/3 from windows, you'll need to get this:
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

