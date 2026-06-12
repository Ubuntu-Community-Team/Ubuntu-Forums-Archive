---
title: "Configuring 2nd Drive"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by Timmoore001 on 2014-04-20
Now I'm building a computer based on Ubuntu 14.04.

Its intended to use a SanDisk SSD 256GB Ultra Plus as a very fast affordable drive for the operating system, But I want to use a WD 1TB drive for the bulky data viz:- Music, Films. Atchives etc.

now the question is:-

Whats the neatest way of have a folder on the Desktop that will allow me to drop bulky data on the 2nd drive? and return gracefully to the SSD drive.

(I'm hoping the the speed of the SSD for 90% of my day by day activity, but keep it uncluttered of vast collection of files)

Hope all that makes sense !   Maybe there is a better way of configuring a SSD based computer.

Any thoughts very welcome !

Tim

---

### Post by Mark_in_Hollywood on 2014-04-20
Please have a look here. I believe it's a leg up for you.

[http://askubuntu.com/questions/379205/installing-programs-in-root-vs-home-partitions](http://askubuntu.com/questions/379205/installing-programs-in-root-vs-home-partitions)

---

### Post by Timmoore001 on 2014-04-20
Many thanks !  I study that very carefully !

[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Tim

---

### Post by oldfred on 2014-04-20
I installed a SSD two years ago. It is 64GB and I have two root partitions. Currently my working 12.04 and as of yesterday my new 14.04 future working install once fully configured. Each in about 28GB.
My 12.04 install uses 11GB of the 28GB and my /home is 2GB mostly .wine with Picasa.

I link all data including some hidden files & folders like Firefox & Thunderbird into data partitions on my rotating drive. I primarily do the common data partition as I have multiple installs, mostly just testing but want to be able to access all the same data from every one of them.

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by Timmoore001 on 2014-04-21
Many thanks for the info !  Its going to take a day or so to absorb all of that.

I'm sure what I need is in there !  So greatly appreciated !

[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Tim

---

### Post by oldfred on 2014-04-21
Post #4 in first link has the commands I use. You just can copy them with your name for your data partition or just use data like I do and your UUIDS.
But you should read discussion for better understanding of pros & cons. I have used linked partitions for several years.
The only time I had an issues with my links was when I thought I had not linked a partition and put the link in the actual partition. It converted my actual data partition to a link and I did not know how to undo that and had to recover data from backup.

---

### Post by Timmoore001 on 2014-04-21
I've used Kate to store a copy of the code in #4 ready for use !  Makes a lot of sense to me but I'm also learning a lot especially from your help !

Currently I use a Directory I made called '0My Everything' to keep any data in a large series of sub-Directories such as 'My Photos'.  I intend to use your code to move this to the 2nd Hard Disc and keep all the programs on the SSD.

Seems to make sense to me !

Is there a neat way to automatically send any additions and changes to this directly automatically yo the cloud 'Adrive' ? (After all Ubuntu One is about to expire...)

Currently a very happy,

Tim

---

### Post by oldfred on 2014-04-21
I do not use cloud, but backup to another hard drive and burn DVDs for most important data on a regular basis.

I do not recommend spaces with Linux. It just makes things more difficult as you have to either add quotes around the name, or escape with \ or \040 so it knows you have a space.

I find using CamelCase, under_score, or justaname work for me. I converted to that in XP years ago and it makes it a lot easier.

---

### Post by Timmoore001 on 2014-04-21
I think I'll rename it '0My_Everything'  as the last thing I need is to make it even harder to get stuff to work !  *LOL*

[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]


Tim

---

