---
title: "Formatting during install"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by prolix on 2007-09-25
I'm trying to install Gutsy on my Core 2 Duo Thinkpad T61. I finally booted into the LiveCD, and started the install. When it came to partitioning, I chose the manual option, because I have vista installed to a one partition and I want to dual boot to Vista and Ubuntu. So I have my Vista partition, a FAT32 partition to share between the two OSes, a 1.5GB swap partition, and then my ext3 partition for Ubuntu. Anyway, I go through the manual partitioning and select the ext3 partition for the root filesystem. I finish up the rest of the steps, it starts installing...and freezes at 5%, while creating the ext3 file system. I've tried several times, with the same results. Upon some Googling, I read that I should try running "sudo ubiquity" from a command line rather than double-clicking the icon on the desktop. Neither way works. Any ideas what's causing it to freeze, and what I can do to fix it?

This computer is literally brand new (about 3 days old). Vista runs just fine. I doubt it's a bad HDD, although I suppose that's possible.



Some specs:

160 GB hard drive, 2.4GHz Intel Core 2 Duo processor, 3GB RAM

---

### Post by Pumalite on 2007-09-25
You first have to partition using Vista's partitioner. Then install using Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'.

---

### Post by prolix on 2007-09-25
Why do I need to use Vista's partitioning? I already created the appropriate partitions using gParted before installing Vista. It doesn't seem like there's any more partitioning to be done, just formatting the ext3 partition.

---

### Post by prolix on 2007-09-25
Also, after wrestling with 7.04 for a while with even less success, I read here: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61") that it's better to just go with Gutsy Gibbon. Is there an alternate CD for Gutsy?

---

### Post by dunnerz on 2007-09-28
This happened for me too

I already have dapper installed (yes, I know, I'm behind the times), and wanted to clean installed gutsy.... So used manual partition, selected only to format "/", but it freezes at 5% - incidentally, it did actually format the drive!!

Any ideas?

---

### Post by dabl on 2007-09-28
I'm guessing, kinda, but a lot of these "freezes at xx%" installation issues end up being a bad installation CD.  You might want to eliminate that possibility by slow-burning a new installation CD at 4X speed.  :)

---

### Post by wpshooter on 2007-09-28
> **prolix said:**
> Also, after wrestling with 7.04 for a while with even less success, I read here: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61") that it's better to just go with Gutsy Gibbon. Is there an alternate CD for Gutsy?

I really doubt that you would be better off with Gutsy at this time !!!

---

### Post by wpshooter on 2007-09-28
> **dabl said:**
> I'm guessing, kinda, but a lot of these "freezes at xx%" installation issues end up being a bad installation CD.  You might want to eliminate that possibility by slow-burning a new installation CD at 4X speed.  :)

I agree.

As I have asked probably a million times before, have you checked the integrity of the Ubunut CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by prolix on 2007-09-28
I found the problem.

I tried an install using the alternate CD, and while attempting to partition it claimed to be unable to mount the Windows partition, for some unspecified reason, and was hung up waiting for me to tell it what to do. So I went back to the Ubiquity (GUI) installation, and when I manually assigned partitions, as before, I told it not to mount the Windows partition (blank mount point). Hey presto, it installed, and now I have a (mostly) working Ubuntu (I'm having some trouble with TwinView, but that's neither here nor there).

It seems that Ubiquity simply fails to inform the user of its error, and that's why it hung.

---

### Post by bgturk on 2007-09-28
> **prolix said:**
> I found the problem.

I tried an install using the alternate CD, and while attempting to partition it claimed to be unable to mount the Windows partition, for some unspecified reason, and was hung up waiting for me to tell it what to do. So I went back to the Ubiquity (GUI) installation, and when I manually assigned partitions, as before, I told it not to mount the Windows partition (blank mount point). Hey presto, it installed, and now I have a (mostly) working Ubuntu (I'm having some trouble with TwinView, but that's neither here nor there).

It seems that Ubiquity simply fails to inform the user of its error, and that's why it hung.

Thanks! This work around solved the hang for me. However, I will now have to add the windows partition to fstab manually. :-(

---

