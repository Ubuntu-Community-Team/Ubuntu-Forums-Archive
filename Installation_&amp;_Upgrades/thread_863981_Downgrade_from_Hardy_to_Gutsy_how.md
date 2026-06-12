---
title: "Downgrade from Hardy to Gutsy: how?"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by project4 on 2008-07-19
Hi I have a HP pavillion dv6300 laptop. When I bought it at the beginning of the year I immediately removed Vista and put Gutsy on it.

It worked very well. 

I happily upgraded to Hardy expecting something that would blow me away. I am patient, updating everyday avg 10 installations. I dont even know if I am supposed to.. or only to do the security ones...

Anyways bottomline: my laptop has become slower. It starts up slower. I turned of the compiz fusion to make it faster. That helped a bit... but I hear the hard drive rattling all the time. as if its a windows machine that gets slower.

I want to go back to Gutsy which I thought worked well and fast. But I dont want to back up all my files music etc on 20 cd's.

Is there a way (commandlines) to downgrade easily to Gutsy? Thanks. 

And one last note: I believe in Ubuntu and open source software, open standards and interoperability. It's part of my job too... I am sure that Ubuntu will come up with a better release. But for now: How can I get back to Gutsy?

Thanks.

---

### Post by flytripper on 2008-07-19
re install gutsy

---

### Post by wannadumpwindows on 2008-07-19
There's no easy way to "downgrade".

Sorry to be the one to break the bad news, but you're gonna have to back-up and re-install.:(

---

### Post by stchman on 2008-07-19
> **project4 said:**
> Hi I have a HP pavillion dv6300 laptop. When I bought it at the beginning of the year I immediately removed Vista and put Gutsy on it.

It worked very well. 

I happily upgraded to Hardy expecting something that would blow me away. I am patient, updating everyday avg 10 installations. I dont even know if I am supposed to.. or only to do the security ones...

Anyways bottomline: my laptop has become slower. It starts up slower. I turned of the compiz fusion to make it faster. That helped a bit... but I hear the hard drive rattling all the time. as if its a windows machine that gets slower.

I want to go back to Gutsy which I thought worked well and fast. But I dont want to back up all my files music etc on 20 cd's.

Is there a way (commandlines) to downgrade easily to Gutsy? Thanks. 

And one last note: I believe in Ubuntu and open source software, open standards and interoperability. It's part of my job too... I am sure that Ubuntu will come up with a better release. But for now: How can I get back to Gutsy?

Thanks.
Did you do a clean install of Gutsy?  If no then that is most likely your problem.  DO a clean install.

---

### Post by Sef on 2008-07-19
> Did you do a clean install of Gutsy? If no then that is most likely your problem. DO a clean install.

There are less problems with clean installs than upgrades.

---

### Post by Partyboi2 on 2008-07-19
> I want to go back to Gutsy which I thought worked well and fast. But I dont want to back up all my files music etc on 20 cd's.
You could create a seperate storage partition before you reinstall gusty and move over all your data you want to keep. This could save you 20 cds :)

---

### Post by stchman on 2008-07-21
> **Sef said:**
> There are less problems with clean installs than upgrades.
A clean install is actually faster than an upgrade.  I can install Ubuntu in about an hour.

---

### Post by project4 on 2008-07-30
> **Partyboi2 said:**
> You could create a seperate storage partition before you reinstall gusty and move over all your data you want to keep. This could save you 20 cds :)

Thanks so much everyone. I could start this thing this evening. What is the procedure for creating the separate partition? And how do I move all the data after that? 

I am not so experienced with partitioning etc...
Thanks!

---

### Post by kspncr on 2008-07-30
> **project4 said:**
> What is the procedure for creating the separate partition? And how do I move all the data after that? 


You'll have to boot the Ubuntu live cd and run the partition editor (GParted) under system->administration.

Then you'll want to shrink your partition and use the empty space (left over from shrinking the Ubuntu partition) to make a new partition (ext3 format should do, unless you favor FAT32 for some reason or another). Make sure the Ubuntu partition comes before the new one. After you've created the new partition, boot back into Ubuntu and copy all the files you want to save onto the new partition. Re-install Ubuntu on the old partition. If you want, you can then re-copy all your saved files back to the first partition, delete the newer partition, and extend the Ubuntu partition to take up the rest of the space (again, with GParted).

However, there is an important thing to mention here: there are always risks when partitioning hard drives, so it's always advised that you back up your stuff before you partition. But, you're trying to save yourself 20 CDs in the first place, so moving all your stuff onto a new partition may not be the best course of action. The choice is yours, and good luck.

---

### Post by project4 on 2008-08-02
> **kspncr said:**
> You'll have to boot the Ubuntu live cd and run the partition editor (GParted) under system->administration.

Then you'll want to shrink your partition and use the empty space (left over from shrinking the Ubuntu partition) to make a new partition (ext3 format should do, unless you favor FAT32 for some reason or another). Make sure the Ubuntu partition comes before the new one. After you've created the new partition, boot back into Ubuntu and copy all the files you want to save onto the new partition. Re-install Ubuntu on the old partition. If you want, you can then re-copy all your saved files back to the first partition, delete the newer partition, and extend the Ubuntu partition to take up the rest of the space (again, with GParted).

However, there is an important thing to mention here: there are always risks when partitioning hard drives, so it's always advised that you back up your stuff before you partition. But, you're trying to save yourself 20 CDs in the first place, so moving all your stuff onto a new partition may not be the best course of action. The choice is yours, and good luck.

Thanks!

---

### Post by Posterus on 2008-08-08
> **stchman said:**
> A clean install is actually faster than an upgrade.  I can install Ubuntu in about an hour.

if you read the post, he is trying to DOWNGRADE not UPGRADE

---

