---
title: "Help with partioner"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by Transmit on 2006-09-26
Hi everyone,

I've been trying to install ubuntu for a couple of days now but I still haven't got any luck in getting it to work.
My problem is this:
I got 1 HD(100GB, 60GB used) that already has Windows XP pro on it. Now I read on the website about how the installer has a partioner. So I put in my ubuntu cd and reboot. The cd boots and I can chose a couple of things where one of them is: Install/startup ubuntu.

I ofcourse chose that one. An ubuntu desktop opens with a map on it called "examples" and an installer called "install". I click the installer and go trough the steps untill I end up with the partioner. 

pic:
[http://www.ubuntu.com/include/testing/flight6/espresso6-small.png](http://www.ubuntu.com/include/testing/flight6/espresso6-small.png)

I chose to manually edit the partition table.

Then I get the window where it shows my hard drive and how much space is used and free. Now this is where I'm stuck. Can someone guide me trough the rest please?

for the record: I want to keep my xp and all the files with it!!

---

### Post by slimb on 2006-09-26
the partitioner itself gave me problems with XP.  it didn't like the NTFS partition.

so i did what the wiki suggested here :

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

there is a section called 

> Issues with Windows XP and NTFS

i followed those instructions first - using qparted it was simple, it gave me a graphical interface - i chose my windows partition and decided i only wanted it to be its current size + 5gb (its a work laptop - i wont need much more than that) and then i created a new partition with what was left.  

then i ran the ubuntu installer again and the partitioner did its thing automagically (i chose to let it partition for me).

---

### Post by bigken on 2006-09-26
Backup your data 1st then defrag windows use [this ]("http://gparted.sourceforge.net/livecd.php")to partion your drive  then run the install select custom partion and use the free space ;)

---

### Post by Transmit on 2006-09-26
So what that page is saying is that I need to resize my windows partition (it's now my full HD) and the I can put ubuntu on the rest of the HD wich was the part I excluded from my partition for XP?

Is that all or do I need to do something else after that?

---

### Post by bigken on 2006-09-26
yep its much easier if you use the gparted liveCD less chance of making any mistakes and you must defrag 1st (in windows) ;)

---

### Post by Transmit on 2006-09-26
> **bigken said:**
> Backup your data 1st then defrag windows use [this ]("http://gparted.sourceforge.net/livecd.php")to partion your drive  then run the install select custom partion and use the free space ;)


"Partion your drive", is that the same as just making my windows XP partion smaller? 
and the space left is the space I put my ubuntu install on?

Sorry for all the questions but I don't wan't to screw up.

MANY THANKS ALREADY!!!

---

### Post by bigken on 2006-09-26
> **Transmit said:**
> "Partion your drive", is that the same as just making my windows XP partion smaller? 
and the space left is the space I put my ubuntu install on?

Sorry for all the questions but I don't wan't to screw up.

MANY THANKS ALREADY!!!

yes but this works much better using the gparted liveCD I have give you the link too

---

### Post by bigken on 2006-09-26
and please backup  your important data 1st ;)

---

### Post by Transmit on 2006-09-26
is there a way to backup in windows without using a stupid floppy disk because my laptop doesn't have one...

---

