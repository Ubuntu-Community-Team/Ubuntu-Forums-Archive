---
title: "Maverick hangs during installation"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by EthioJOB on 2011-01-22
Hi.

Recently I got me a newly assembed PC and I tried to install Maverick alongside Windows 7. However, while the Live CD works and I was able to partition my hard disk, just when the installation copies after a number of files and says 'ready when you are' (right after I finish entering my username and password), it won't budge from there. I've tried twice to no avail. I'm thinking of trying Lucid instead. What is the problem?

I've partitioned the HD inwo three partitions - 74 GB for windows, 300 GB for the intended Ubuntu, and the remaining 80 something for ArtistX. (The last two partitions are in ext3)

Here are some of my PC's specs, just in case.

Intel Dual Core E5200 2.5 GHz
467 GB HD
2GB RAM
Gigabyte motherboard G31M-ES2C with Intel Chipsets

---

### Post by Rubi1200 on 2011-01-22
If you entered a user name that contains an uppercase letter, the install will freeze.

Example:

Your Name: John Smith

User Name: needs to be john NOT John

Quick question: which option did you choose to install with? Manual or Alongside?

There is a bug in the 10.10 installer that *may* wreck other operating systems.

---

### Post by EthioJOB on 2011-01-22
Well, well, I just might have found the problem. I actually did use upper case letters. I'll fix that right now.

I used the manual installation option because I want to select the second partition for ubuntu without touching the third. This bug you mentioned sounds kind of risky. Tell me, am I better off with 10.04, or is it safe once I use the option you are going to recommend? (because selecting alongside evidently will use all the remaining space regardless of the partition)

Thanks.

---

### Post by Rubi1200 on 2011-01-22
If you use the manual partitioning option then you should be good to go (and it sounds like you know what you are doing anyway).

For more about the problems I mentioned, see here:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Especially here:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

Good luck and let me know if you need any other help.

---

### Post by EthioJOB on 2011-01-22
Well, i've got a few questions i'd like answered before i proceed.

1. Generally speaking, what is the consensus on choosing between Maverick and Lucid? (i've got both CDs)

2. Is the user name the only field I should take care in not using uppercase letters? what about my name and computer name? (just to make sure there are no issues here as well)

3. About the partitions, which filesystem is better for me to use, ext3 or ext4?

Thanks in advance.

---

### Post by Rubi1200 on 2011-01-22
> 1. Generally speaking, what is the consensus on choosing between Maverick and Lucid? (i've got both CDs)Lucid is an LTS release, meaning it is supported on the Desktop for 3 year (until April 2013).
Maverick only has support for 18 months.

Personally, I think if you are looking for stability, go for Lucid

>  2. Is the user name the only field I should take care in not using  uppercase letters? what about my name and computer name? (just to make  sure there are no issues here as well)As far as I am aware, yes. You also need to make sure you use a password that meets the minimum requirements.

> 3. About the partitions, which filesystem is better for me to use, ext3 or ext4?The default since 9.10 has been ext4 and although you will hear different views, I think it is best to go with the default.

Feel free to ask as many questions as you like before proceeding.

---

### Post by EthioJOB on 2011-01-22
Thanks. I'll proceed with what I've got so far and I'll come back if there is any further issues.

---

