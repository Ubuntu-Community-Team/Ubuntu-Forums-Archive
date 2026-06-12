---
title: "XP and Ubuntu"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by ttiell on 2008-02-07
I've seen other posts talking about having dual boot for XP and Ubuntu.  I've tried and failed at this.  I lost a lot of stuff on my XP (only about 80% backed up).  I now have XP up and running again.  It took about a week to re-load all of my programs and debug XP all over again.

Now I would like to give another crack at Ubuntu.  Is there any kind of "How To" out there?  My current system is XP on an IDE hard drive.  I have an extra IDE hard drive to install Ubuntu.  What is the best way to go about this?

---

### Post by rustyjr on 2008-02-07
What I did was partition my hard drive into 3 drives. Ex: 40GB -29.5 GB XP 10 GB linux .5 GB swap
I fomatted the two larger drives then installed XP. I then refomatted with ubuntu the 10 GB and swap. now I have a dual boot computer

---

### Post by ttiell on 2008-02-07
I need more of a step by step instructions.

Previously:  I installed XP 150GB (partition 0) - worked good.  Installed WinGrub onto XP partition - worked good.  Installed Alternate CD of Ubuntu 7.10 (Live CD wouldn't work) 40GB (partition 1) with swap 2GB (partition 3). ------- Everything goes to crap.  Computer starts into BIOS, acts like it is going into a program and then restarts everytime.

But don't try to fix that problem, others have tried and it never worked.

So now I have reformated everything, put XP on the whole drive and bought a used drive to have for Ubuntu.

I need more detail on how to do this because I don't want to have to start over again.

---

### Post by jan quark on 2008-02-07
you can follow this guide

it is good to install xp first and then ubuntu
create an blank partition in xp
and install ubuntu on this partition using the option "install on largest continuous free space" during the partition step of the installation process

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by Support the 2nd on 2008-02-07
I did this last year and had serious issues.  If you can search for my posts on the subject (i haven't posted much here lol so there are not many) you might find some useful information.

Basically, there was a couple boot files (MBR?...Grub?) that got messed up on the XP harddrive because Linux overwrote the XP file even though I thought I had told it not to while installing on the second HD.  Long story short, if I recall, I unhooked my XP hard drive while installing Ubuntu, then unhooked my Ubuntu drive while reinstalling XP.  I believe that cured the corrupted/missing boot file issue.

---

