---
title: "Separate partition for /home folder"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Danimoth on 2009-12-26
I have an installation of ubuntu that uses an entire HDD. I want to have a separate partition for the /home folder, so i can format the other without risk of losing my personal files. Also, a friend told me that if i upgrade to a newer ubuntu version while also keeping my home folder intact, all settings(and not just files will be kept).

Therefore I am looking for a way to create a seperate partition for the /home folder without reformatting. 
So far i have found that i can make a boot CD with gparted and create/resize partitions as i want. I am not sure, however, how to move the home folder to the new partition and what to do with the mount point. For example, i get the impression that i won't be able to move the home folder since some files will be in use because i will be logged on. 

Any help is appreciated.


:popcorn:

---

### Post by raymondh on 2009-12-26
> **Danimoth said:**
> I have an installation of ubuntu that uses an entire HDD. I want to have a separate partition for the /home folder, so i can format the other without risk of losing my personal files. 

I am looking for a way to do it without reformatting. 
So far i have found that i can make a boot CD with gparted and create/resize partitions as i want. I am not sure, however, how to move the home folder to the new partition and what to do with the mount point. For example, i get the impression that i won't be able to move the home folder since some files will be in use because i will be logged on. 

Any help is appreciated.


:popcorn:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Danimoth on 2009-12-26
Guess my search was inadequate :oops:.

Thanx raymondh

---

### Post by raymondh on 2009-12-26
> **Danimoth said:**
> Guess my search was inadequate :oops:.

Thanx raymondh

Have a working/tested back-up of your files before proceeding.

You're welcome :)

---

### Post by Danimoth on 2009-12-26
For the record, the supplied link worked perfectly. I now have a separate home partition :).

---

### Post by phillw on 2009-12-26
> **Danimoth said:**
> For the record, the supplied link worked perfectly. I now have a separate home partition :).

+1

Of course it does - it's written by one of the Mods (Shhh) .... And, yeah, it's a pretty darn kewl How-To.

---

### Post by raymondh on 2009-12-26
> **Danimoth said:**
> For the record, the supplied link worked perfectly. I now have a separate home partition :).

Thanks to AYSIU ;)

---

### Post by badboyengineer on 2010-01-14
> **raymondh said:**
> Thanks to AYSIU ;)

Great thanks to you, Raymondh!

I got my separate /home now!:popcorn:

---

### Post by finlost on 2010-02-02
I was wet behind the ears when I installed my first Ubuntu distro (Hardy).  I didn't create a separate partition for the /home folder.  IIRC, the Live CD wanted to create a separate partition, but I didn't let it.  ](*,)

Two months ago, I did a fresh install of Karmic.  I knew I needed to create a partition for /home.  I didn't pay attention during the install and assumed the Live CD defaulted to creating a separate /home partition.  I assumed incorrectly.  Soon, I will be executing the instructions set forth in this topic.

Question:  Any rule of thumb on the size of each partition?  My HDD is 500GB.  Do I do 250GB for each partition?  

I also have a 300GB USB HDD that stores most of my personal data.

---

### Post by oldfred on 2010-02-02
I had the standard root & swap install for 3 years with only a small windows partition for shared data as we converted from windows to Ubuntu. For Karmic I wanted all the bells and whistles, so I created /home in 9.04 and I created a separate /data. I pretty much copied my history and did the same install on my laptop which had been just windows.

Since I had a new drive on my desktop I created large partitions, but ubuntu is only about 5GB with lots of downloads. My new /home is less than 1GB (of 50GB) since I am linking in all the default directories from my data directory. Of course data is where all my space is used, most now ext3, some NTFS for windows.

Suggest 15-20GB for root, swap equal to RAM memory, /home large if your are storing data there.

Linking in data to home:
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

 [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by finlost on 2010-02-03
Mission accomplished, but I hit a bump along the way.  I received the following message:

```
Could not update ICEauthority file /home/*user*/ICEauthority
```

Per the instructions raymondh linked, I had to enter recovery mode and post the following:
```
chown -R username:username /home/username
chmod 644 /home/username/.dmrc
chmod 644 /home/username/.ICEauthority
exit
```

[IMG]http://www.brews-bros.com/public/style_emoticons/default/frank.gif[/IMG]

All is well now.

---

