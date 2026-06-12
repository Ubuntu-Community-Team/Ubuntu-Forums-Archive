---
title: "Question about home partition"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by DachaArh on 2008-05-16
I installed ubutnu using easy install and managed to get all my hardware working, and now I wan't to fully go to ubutnu, and to leave XP with only some application ( arhichitectural).
And want to have home partition and to transfer all my music, movies etc to that home partition but I do not have enought free space on my hard drive to first create a 80 GB home partition and 40 GB for filesistem ( which is my plan) and then to transfer all my files to home partiton so I wanted to ask you this..
I I format one partition in .ext3 format and make it 80 GB and transfer all my files there, and then make a 40GB filesistem and then start installing ubuntu, will I be able to make a choice of my home partition to be that partition which already have about 40 GB of used space , without having to format that home partition again, and to have all my files there after installing ubuntu...?


thanks alot ;)

---

### Post by forestpixie on 2008-05-16
You won't need 40Gb for the filesystem - I personally use 6Gb, but the most common suggestion I see is for / to be about 10Gb.

Maybe you can then have enough room to move things, perhaps it would if you posted exactly what partitions you have, do this in a terminal

```
sudo fdisk -l
```

I'm not sure whenther you can later call an existing partition as /home as I've never done it, you might be able to.

---

### Post by DachaArh on 2008-05-16
My partitions are now like this :
I have a 160 GB hard drive
C partition 30 GB - windows 
D partition is 70GB - my music
E partiton is 50GB - my docuuments , movies etc...
I would so like that I can call and existing partition as /home it would save me alot of trouble...

I do not think that a 10GB as / would be enought, because I wan't to use wine and to start photoshop and some more application and at this moment with easy install my ubuntu uses 9 GB of C partition and I have only 750MB free there, with wine only installed, with few small application, so I will need at least 20GB for / partition ;)

---

### Post by forestpixie on 2008-05-16
From what I know wine will install in your home partition - I assume you're currently using the wubi thing - I have no idea at all how that deals with it's directory structure :)

Do you know that you can read/write to your existing ntfs partitions from within ubuntu once it's installed?

If I was going to be needing to use a lot of software through wine, I would carry on accessing them through windows instead and dualboot.

Thinking further, I assume that you mean you want Ubuntu to treat an existing ntfs partition as /home, I'm fairly sure that you can't as it will need to be formatted as a linux type filesystem - at that point you will lose the information currently on it. Whichever way you do it you're going to need to get space from somewhere to install to - which partition are you intending to resize?

---

### Post by DachaArh on 2008-05-16
No, I do not intend to have y NTSF partition as /home.
I was going to delete all that is not primary for me, and then to move all from 70GB partition to 50gb partition, and then to format 70GB partition in ext3 to be my /home partition, and then to move all files from 50 GB partition to new ext3 70GB partition and then to format 50GB to ext3 to be my / partition and then try to install ubuntu to 50 gb partition as / partition and 70GB to be home (hoping that all files would be left there and not deleted ) .
Is this possible ?

---

### Post by forestpixie on 2008-05-16
Yes it sounds possible, you can certainly tell the installer to mount a partition as /home in the manual option - and not format it.

I still think that you are making / too big, but that's up to you - I don't know if you can tell wine to install to somewhere else, eg not /home I suspect so.

I would be concerned about the possibility of something happening while I was moving files back and forth to allow the partitions to be used in the way you say.

I assume that you don't have 120Gb of backups :)

If you had an external you could borrow that's what I would do.

---

### Post by DachaArh on 2008-05-16
I do not know anyone with external hard to borrow :( 
you are right wine is installing to /home
but I can't have home larger than 70gb because I will use all in my other 50gb partition to transfer files there before I format 70gb, so I can't add more space to 70GB partition, since there is no more space ...

I have one other idea.
To format 70GB partition to be home, and now from my easy installed ubutnu  to transfer home folder to that partition, and then to install ubutnu. 
I read somewhere that you can move your home folder to new partition, and that way I will keep all my setings from this ubuntu.
Is it possible ?

---

### Post by zhanglini on 2008-05-16
I would keep ntfs, / and /home small, each 10GB maybe.  Then add a FAT32 that takes the rest of the space.  Both winnow$ and Ubuntu will share this partition, and all movies/music/balh blah should go there.
As for /home, I would put only Ubuntu related things (such as settings) there.
I had similar setting when I was dual booting, it worked for me.

---

### Post by forestpixie on 2008-05-16
> I read somewhere that you can move your home folder to new partition, and that way I will keep all my setings from this ubuntu.The method I used was successful but it was before wubi and I doubt if it would work - I'm under the impression that using wubi gives one big file in windows which itself contains the installation eg you don't actually have a /home folder on your windows drives until you open the wubi thing? Stand to be corrected though.

> To format 70GB partition to be home, and now from my easy installed ubutnu to transfer home folder to that partition, and then to install ubutnu.

If you format the partition to be /home as ext3 for example you would need to be able to access the file from within wubi (which itself is within windows) - only way to tell would be to try - but while I know that you can access ext2/3 from within windows I wouldn't be happy about trying to move /home from there even if it was possible.

Good luck

---

### Post by zhanglini on 2008-05-16
> **forestpixie said:**
> I'm under the impression that using wubi gives one big file in windows which itself contains the installation eg you don't actually have a /home folder on your windows drives until you open the wubi thing? 


Yes it is true.  You see /home (for that matter, /etc, /bin whatever) only when you open Ubuntu.

---

### Post by DachaArh on 2008-05-16
well I would not still detele my current ubuntu installation, and I would try to move home folder to 70GB partition from within ubuntu..


do you think I can do this ?

---

### Post by forestpixie on 2008-05-16
I'm sorry but I do not know - if you were talking about an ubuntu install I'd say yes - but I don't know if the file that runs as ubuntu in windows would react in the same way as a real installation.

---

### Post by DachaArh on 2008-05-16
> **forestpixie said:**
> I'd say yes - but I don't know if the file that runs as ubuntu in windows would react in the same way as a real installation.


thanks for all your help...

can anyone confirm this ?

---

