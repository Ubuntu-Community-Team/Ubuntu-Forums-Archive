---
title: "Can't update 12.04 to 12.10 &quot;insufficient space on /&quot;"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by way10c on 2013-01-12
I've had a working dual boot of Win7 and 12.04 on separate physical drives for awhile. I wanted to update to 12.10 but whenever I do I get an error that there's not enough space on '/'. It is about 1.7 GB short. Of course, I can't change partition size from w/in 12.04 and Win7 won't touch it. And to add insult, the LiveDVD freezes. Any suggestions?

--Allen

.

---

### Post by malenkylizards on 2013-01-12
What's the size of your hard drive and how full is it?

The answer sounds obvious and simple to me...Copy 2 or 3 GB onto a thumb drive or burn it onto a DVD, delete them from the hard drive, do the update.  Then, when you can, get yourself a 1 TB hard drive, they're only like $50 these days.  Why wouldn't that work?

---

### Post by deadflowr on 2013-01-12
How big is the partition?

And also, maybe probe the system for any caches or files that you can probably clear.

I'd use disk analyzer to get a look at where space is being chewed up.

---

### Post by way10c on 2013-01-12
Ok. I managed to get the main partition reduced 2.79 GB via LiveDVD but it would not increase the '/' partition at all (well 1MB but that's it) before it stopped working.

--Allen

.

---

### Post by way10c on 2013-01-12
I've been able to open up space twice (see attached screenshot) but I can't figure a way to use the available space to add to the '/' partition.

--Allen

.

---

### Post by darkod on 2013-01-13
As you can see clearly, you have the /home partition between the / partition and the 9.77GB unallocated space you created. How do you plan the / partition to expand with it when they are physically not next to each other?

The unallocated space needs to be next to it. And by the way, starting of with a / of only 6.5GB was a very bad idea.

On the other hand, you don't even need to upgrade to 12.10 unless there is some good reason. Not only because it's the latest version. 12.04 is LTS and will have long term support, I would stick to it personally.

---

### Post by way10c on 2013-01-17
Greetings,

Thanks for the response. 

I've actually solved the problem. (gpart live CD is my new friend!) It took me a bit to figure out how the Move Partition function works. I was then able to move the unallocated space I stole from the rear end of my main partition to between the main partition and the "/" partition before expanding "/" into the unallocated space.

>>And by the way, starting of with a / of only 6.5GB was a very bad idea.

Actually, 6.5 GB was about twice the recommended size when I first installed Ubuntu a few versions back.

As to why I updated. Yes I do like to stay up-to-date. I also watch a fair number of youtube vids and got sick of the persistent inverse color bug in 12.04. My son tells me 12.10 fixed that.

Thanks again.

--Allen

.

---

