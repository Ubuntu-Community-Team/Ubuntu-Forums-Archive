---
title: "Ubuntu 10.10 partitioning ?"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2011-09-08
I feel I am loosing control of my computer. It started with clicking on thunderbird icon 1x and getting at least 2 pages. Today trying to center text in excel was a problem. Text went to left instead of the center. After several tries got the text in the middle. Highlighting text I want is a problem and there are other problems. 

Thus decided to reinstall ubuntu with disk ubuntu 10.10. System requirement is 2.6GB. I have 75.2GB thus it should of been no problem. Got message:
Failed to partition the selected disk. This may be due to lack of space.

Logically seems I should manually partition the disk but that is beyond my knowledge without help. Can someone tell me how to manually partition the disk?

---

### Post by haqking on 2011-09-08
> **Camilia said:**
> I feel I am loosing control of my computer. It started with clicking on thunderbird icon 1x and getting at least 2 pages. Today trying to center text in excel was a problem. Text went to left instead of the center. After several tries got the text in the middle. Highlighting text I want is a problem and there are other problems. 

Thus decided to reinstall ubuntu with disk ubuntu 10.10. System requirement is 2.6GB. I have 75.2GB thus it should of been no problem. Got message:
Failed to partition the selected disk. This may be due to lack of space.

Logically seems I should manually partition the disk but that is beyond my knowledge without help. Can someone tell me how to manually partition the disk?


FRIST backup all data

Choose automatic in which case it should do it for you.
or manual partition and have one for / and one for /home

on a home system not much need for others though i have seperate /tmp /boot/ / /home /usr and /var

but usually overkill

or do the whole thing as /

or the disk is mounted in your current OS which is why you cant

---

### Post by Camilia on 2011-09-08
> **haqking said:**
> FRIST backup all data

Choose automatic in which case it should do it for you.
or manual partition and have one for / and one for /home

on a home system not much need for others though i have seperate /tmp /boot/ / /home /usr and /var

but usually overkill

or do the whole thing as /

or the disk is mounted in your current OS which is why you cant
You have totally confused me. As I stated I chose manual partition and it didn't work.

---

### Post by haqking on 2011-09-08
> **Camilia said:**
> You have totally confused me. As I stated I chose manual partition and it didn't work.


sorry.

Simply put if you are confused then at least make sure that you have all your data backed up and do an automatic and not manual then.

as long as you are not dual booting etc and dont have anything else on the drive.

---

### Post by Camilia on 2011-09-08
> **haqking said:**
> sorry.

Simply put if you are confused then at least make sure that you have all your data backed up and do an automatic and not manual then.

as long as you are not dual booting etc and dont have anything else on the drive.
I am going to do a backup before I do anything. As I told you I can't get the computer to a manual restore. Which is why I am asking for help to partition.

---

### Post by haqking on 2011-09-08
> **Camilia said:**
> I am going to do a backup before I do anything. As I told you I can't get the computer to a manual restore. Which is why I am asking for help to partition.


What is it on there right now ? windows ?

As for partitioning like i said if you are unfamiliar then there should be an option during install to do it automatically.

if not and you have to do it manually then just do one big partition and when it asks you how you want to mount it you choose or type the /

which is the root partitioon.

you should probably have a seperate one for /home also but i dont want to confuse you as you sound like you are very new to this ?

cheers

and read here [http://ubuntuone.com/6snmL8cnGbpYPBegqcHrnr](http://ubuntuone.com/6snmL8cnGbpYPBegqcHrnr) which is from [anewguy]("http://ubuntuforums.org/member.php?u=331304") who created a guide with partitioning in it ;-)

---

### Post by Camilia on 2011-09-08
> **haqking said:**
> What is it on there right now ? windows ?

If you have to do it manually then just do one big partition and when it asks you how you want to mount it you choose or type the /
which is the root partition.

I have ubuntu 10.10. Did upgrade wia update manager. Needed to copy and restart, for in spreadsheet cursor is not working properly. Constantly have to redo something or erase duplicate.

Now I understand. Unclear as to what I should type though in the 2 partitions.

---

### Post by haqking on 2011-09-08
> **Camilia said:**
> I have ubuntu 10.10. Did upgrade wia update manager. Needed to copy and restart, for in spreadsheet cursor is not working properly. Constantly have to redo something or erase duplicate.

Now I understand. Unclear as to what I should type though in the 2 partitions.


have a read through the guide first.

so you have 2 partitions ? you created these yourself ?

basically to be used they need to be mounted, / or root which you specify by calling it / or mounting it as / is the minimum config you need then everything gets installed into that unless you specify additional partitions for other mount points.

so for example you might want to put your home directory in another partition with /home

it will be transparent to you when using your system as linux treats partitions as mount points so all appear in the filesystem as directory.

---

### Post by Camilia on 2011-11-10
Well my mouse stopped working. Got a new 1 and now no problems.

Also got info on cloning. That will be next project for PC.

---

