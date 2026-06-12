---
title: "To Software Raid or Not to Software Raid, that is the Question"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by ajfletcher on 2010-05-31
Hello all, I am in the process of setting up my first Ubuntu LAMP server.  It will be used to host 4 websites, with a combined monthly bandwidth of 60-80 GB, of outbound traffic.  Now I have been running on a dedicated centOS server with cPanel for the last two years but am now taking the plunge to run my own system utilizing the CLI.

Now my question is as follows, the server is coming with two 160GB HD,  initially my thought was to put the  /swap /boot /usr and /var on drive 1 and /home on drive 2 for the best usage of the drives, but after doing some reading I found out that software RAID with Linux seems to be pretty reliable.   

RAID 0 seems to risky to me as you double your chances of a complete failure, granted you get fast reads and writes but I am not sure its worth it.

RAID 1 though does offer benefits but I guess since you are writing all data in parallel you lose write speed.

I guess my question is, does software RAID 1 slow the system down enough to make it unpractical in a LAMP environment?   One of the websites uses vBulletin / wordpress pretty heavily, with the other two using WordPress.

One last question,  does Ubuntu Linux recognize external USB drives?  Was considering using one as a backup drive

---

