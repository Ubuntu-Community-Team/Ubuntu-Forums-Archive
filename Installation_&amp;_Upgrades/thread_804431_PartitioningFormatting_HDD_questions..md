---
title: "Partitioning/Formatting HDD questions."
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by rptizzle on 2008-05-23
Okay, I'm a long time Windows user trying to switch to Linux so I can be a truly free soul.

I have gotten frustrated with this issue and after hours of browsing the Forum (not a real useful way to spend my precious time) for an answer I decided to post my questions to see if I can more quickly get some answers.

I just built a new computer with an AMD64 chip and it looks awesome. My friends are telling me to install Vista, but I went ahead and installed Ubuntu 64. That means I went into Linux cold turkey.

Ubuntu is running beautifully, but I am not sure how to format the other partition and use it. I have a bunch of questions and here they are:

1) My primary drive is 250 GB of capacity and I created a partition of 20 GB for Ubuntu (someone on the Forum said that should be enough). GParted shows that partition as /dev/sda1. I set up the home folder to partition /dev/sda2. I did that because I assumed the new files I save and download will go into the home folder, and so I'd like those files to be separate from the OS. I always want my OS to be separate from my personal files - it's a bit difficult to do that in Windows, but my familiarity with Windows allows me to do that just fine.
Anyway, here's the issue: I cannot find the second partition! Where would it be??? I click on Places -> Home Folder. There's a panel on the left titled Places. It shows "ricardo, Desktop, File System, Network Servers and Trash". I am assuming that File System is the system drive where Ubuntu is installed. 

I

---

### Post by fuzzyk.k on 2008-05-23
your second patiton is mounted on /home
i

---

### Post by HunterThomson on 2008-05-23
> **rptizzle said:**
> Okay, I'm a long time Windows user trying to switch to Linux so I can be a truly free soul.

I have gotten frustrated with this issue and after hours of browsing the Forum (not a real useful way to spend my precious time) for an answer I decided to post my questions to see if I can more quickly get some answers.

I just built a new computer with an AMD64 chip and it looks awesome. My friends are telling me to install Vista, but I went ahead and installed Ubuntu 64. That means I went into Linux cold turkey.

Ubuntu is running beautifully, but I am not sure how to format the other partition and use it. I have a bunch of questions and here they are:

1) My primary drive is 250 GB of capacity and I created a partition of 20 GB for Ubuntu (someone on the Forum said that should be enough). GParted shows that partition as /dev/sda1. I set up the home folder to partition /dev/sda2. I did that because I assumed the new files I save and download will go into the home folder, and so I'd like those files to be separate from the OS. I always want my OS to be separate from my personal files - it's a bit difficult to do that in Windows, but my familiarity with Windows allows me to do that just fine.
Anyway, here's the issue: I cannot find the second partition! Where would it be??? I click on Places -> Home Folder. There's a panel on the left titled Places. It shows "ricardo, Desktop, File System, Network Servers and Trash". I am assuming that File System is the system drive where Ubuntu is installed. 

I

It sounds like you just left the rest of the hard drive as free space. Here is a link to a ansore to a partition question that I just posted. It shows how to make a /home partition for all your saved games and music, docs, desktop, users, settings. This is a vary good Idea. I have a 150mb /boot, 20GB /, 220GB /home.
[http://ubuntuforums.org/showthread.php?p=5023820#post5023820](http://ubuntuforums.org/showthread.php?p=5023820#post5023820)

---

### Post by HunterThomson on 2008-05-23
here is how it should look if you have more then one partition.

---

### Post by Trebaruna on 2008-05-23
Find yourself a terminal (Applications - Accessories - Terminal OR <Alt+F2> and type gnome-terminal) and issue the command "mount" without the quotes.
Look for a line like this one:

/dev/sda2 on /home type ext3 (rw,relatime)

The stuff between parentheses doesn't matter here. What matters is /dev/sdaX (where X is partition number) denoting the partition, and /home (or whatever after "on") denoting where in the filesystem tree it was mounted.

If you have a device mounted as /home, you're all set. Linux will write everything you put in /home or any of its subdirectories on your separate partition, and in the event you need to reinstall you can just plug it back in.

---

