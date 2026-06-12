---
title: "Question about /Home"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by kholdstare311 on 2007-07-08
Im back with another extremely stupid question: Is the /Home directory where all my saved documents and installed program files and such would go? I've never seriously used Linux before so I really have no idea...

---

### Post by taurus on 2007-07-08
All your personal settings will go into /home/**john**, _assuming_ **john** is your login name.  You can do whatever you want with your $HOME directory.

---

### Post by obrient on 2007-07-08
/home is where documents are usually saved. Think of it as "My documents". /usr I believe is where most programs get saved. 

Definitely still learning also :)

---

### Post by merlinus on 2007-07-08
Most programs are NOT saved in /home, but configurations and preferences are.  And you can create subdirectories for data, as already suggested.

-merlin

---

### Post by christhemonkey on 2007-07-08
And remember no question is a sillly question, there are only silly answers!




*(unless it genuinely is a silly question...)*

---

### Post by kholdstare311 on 2007-07-08
Okay, so since it's like a My Documents folder, then could I use the shared FAT32 partition on my drive to store /Home as well as my windows Documents, or does the separate /Home partition have to be Ext3?

---

### Post by kholdstare311 on 2007-07-08
Anyone?:confused:

---

### Post by merlinus on 2007-07-08
If you want /home to be mounted as a separate partition in ubuntu, then it needs to be formatted as a linux filesystem (e.g. ext2, ext3, reiserfs).

But you can use a FAT32 partition to share files.  It will be mounted as /media/fat32, or something like that, depending upon what you choose.

I have had great success writing to and from ext3 partitions from windows using the ifs driver at:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

-merlin

---

### Post by christhemonkey on 2007-07-08
You can use FAT32 for a /home partition yes.

---

### Post by kholdstare311 on 2007-07-08
Okay so what you're saying is that if I want /Home separate from /, I have to create another Ext3 partition?

Either way works for me, I suppose. How large of a partition would you suggest I use for /Home?

---

### Post by kholdstare311 on 2007-07-08
If I have my partitions set up as such:

Windows - 20gig
/ - 10gig
/Swap - 1 gig
/Shared - ~45 gig

How much do you think I should shave off of the Shared partition to make way for /Home? I just want Home to store my settings and appearence settings and such, and perhaps the files I save while learning how to code - my text, music, video, etc files will all be on the shared partition.

PLEASE help, I'm partitioning my drive right now and need to know.

---

### Post by merlinus on 2007-07-08
It is difficult to come up with an arbitrary figure for a /home partition, since it depends upon how much free space is available, and how much data (and kinds of files) you intend to store there.

But because a separate /home partition will store settings, configurations, preferences, email, bookmarks and such, it is very much worthwhile.

Then, when you have to reinstall (or install a new version of ubuntu) as I had to do yesterday, things will go much easier in terms of setting up your apps.

Note:  I just saw your last post.  I would give 15G or so to /home, since you may decide to store certain kinds of files there at some point.  And also, if you need more room for /, it will be easier to shrink /home and add the freed-up space to /.

-merlin

---

### Post by kholdstare311 on 2007-07-08
THank you for the suggestion. I'll go with that for now, and I assume I should be able to shrink and fiddle with the other partitions in the future if anything changes drastically. Like i said, settings on /Home will store settings and small files (no emails there), and Shared will store most files. Most of my multimedia will be on external drive anyway.

---

