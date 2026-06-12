---
title: "Raid 5"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by thecaptainjs on 2008-02-03
I am building a new PC and would like to setup a raid 5 array. 

Mobo i am going to use that has raid on it: ABIT IP35 Pro LGA

I am looking to triple boot XP, Vista and Ubuntu on an array consisting of:
 4* 320GB seagate 7200.10 drives in Raid 5. 

Haven't used ubuntu in a while so you know. 

Is it possible to set this up so all 3 OS'es are booting off of the raid 5 array? I have heard that you cannot install ubuntu to a raid 5 array!

I was planning on breaking the 960 raid5 into 4 partitions 3 for OS and 1 for data. 


Possible? Feasible?

---

### Post by thecaptainjs on 2008-02-03
!!

---

### Post by thecaptainjs on 2008-02-04
Please Help!!

---

### Post by ajeannotte on 2008-02-04
i'm looking for the same answer.... installing/running Ubuntu from a raid 5 array and looking at a new mobo.

just found this:
[http://ubuntuforums.org/showthread.php?t=662094&highlight=raid5](http://ubuntuforums.org/showthread.php?t=662094&highlight=raid5)

---

### Post by thecaptainjs on 2008-02-05
Yea, i was really hoping that there was a way to boot right off a raid 5 array. 
 I really didnt want to have to boot off another drive. I will have to put an IDE HD in and install ubuntu on that and see if I can get it working.

---

### Post by ajeannotte on 2008-02-05
best you can do is use the raid 5 for data and just make backups of your key install modifications. 

i'd rather lose the OS than all the data. 

still a pain in the *** though.

---

### Post by thecaptainjs on 2008-02-05
Yea, this sucks. Now I dont know if I am going to switch to ubuntu. If I could get it working on the raid array then I would probably switch. Now i dunno, I was planning on using my IDE HD in another PC. 

I cant believe that no one has really made a go at making it work on a raid 5 array...

---

### Post by ajeannotte on 2008-02-05
if you have 4*320GB hard drives, you could leave 3 of them in RAID 5, and one stand alone and end up with the same amount of storage. refreshing the OS once in a while to shake the cobwebs is something i do once in a while anyway. no need to have it redundant. 

Ubuntu is pretty good though. since i've switched i've only gone back a few times to windows for something i didn't have time to figure out how to do in Ubuntu. and then i'd go figure it out when i had time. now, i haven't been back to windows for months.... i think i'm ready to cut the cord.

cheers.

---

### Post by thecaptainjs on 2008-02-05
I wonder if I could install 2 OS'es on the separate drive and the third on the raid array. Use Gag as the boot loader. I'll have to start messing around and see.

---

### Post by ajeannotte on 2008-04-08
I usually keep my OSs on a separate drive, i'm looking at RAID 5 for the data. OSs are easy to replace, data takes time . . . if it can be replaced at all.

here's another thread with some good info that i just stumbled across. Hope it helps.

[http://ubuntuforums.org/showthread.php?t=745131](http://ubuntuforums.org/showthread.php?t=745131)

---

