---
title: "Questions: Install, Upgrade, Backup"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by daksai3 on 2010-08-17
Hi, let me first explain the situation. Right now I'm away from my personal computer (on vacation, and using Dad's laptop). When i return in a few weeks I want to install Ubuntu, but right now I'm doing research on the problems people commonly face with installing and upgrading ubuntu. 


Install Questions:


1. Should I just install Ubuntu 10.04 or the current alpha release? 

2. Is 10.04 the most stable and "best" option riight now? 

3. Should I choose an earlier version? In other words, is it clear of bugs?

4. If my installation is ruined by something like the black screen of death will it affect my other partition, which is Windows 7?

5. I have a 64 bit computer, so should i just get the 64 bit ubuntu? Is it faster than 32 bit? Is EVERYTHING compatible between 32 and 64 bit?


Upgrade Questions:


1. Does Ubuntu still have the problems with upgrading such as having incomplete installs and such that urgently require you to do complete back ups, or are they finally seamless upgrades with only few instances of people with corrupted installations?

2. When you upgrade does it affect your documents (images, music, videos), like deleting them.

3. When you do an upgrade, does it delete your programs such as gimp, google chat, drivers (including 3rd party), etc.?

4. When you do an upgrade, are your settings over written? Like the desktop background, program customizations, and other properties?


Backup Questions:


1. What exactly can you backup? Like, can I backup my documents, programs, and settings?

*What is the home directory? What is it for? Are settings and program installations stored there or something? 


Please answer these questions as accuratly as possible, and personal instances are more than appreciated. Any help is GREAT.:D:

---

### Post by howefield on 2010-08-17
> **daksai3 said:**
> 
1. Should I just install Ubuntu 10.04 or the current alpha release? 
2. Is 10.04 the most stable and "best" option riight now? 
3. Should I choose an earlier version? In other words, is it clear of bugs?
4. If my installation is ruined by something like the black screen of death will it affect my other partition, which is Windows 7?
5. I have a 64 bit computer, so should i just get the 64 bit ubuntu? Is it faster than 32 bit? Is EVERYTHING compatible between 32 and 64 bit?

You should only install the current alpha of Maverick if you expect and want breakage, and specifically have a desire to test, fix and report bugs, otherwise 10.04 being the current LTS (Long Term Support) edition is probably the best bet. 

No one can answer questions 2 and 3 except for themselves and certainly not without knowing what you plan to install it on, specification wise. 10.04 is working beautifully for me, however I am sure there will be someone for which that isn't the case.

Installing Ubuntu should have no effect on your windows install, but use the Live CD or install to USB stick and play around with it for a little while, that may give you an idea of any issues that you might encounter.

Most applications are available in 64 bit, and those that aren't can still be installed using the 32 bit libraries. The notable one is probably flash which you would need to install 32 bit.


> Upgrade Questions:

1. Does Ubuntu still have the problems with upgrading such as having incomplete installs and such that urgently require you to do complete back ups, or are they finally seamless upgrades with only few instances of people with corrupted installations?
2. When you upgrade does it affect your documents (images, music, videos), like deleting them.
3. When you do an upgrade, does it delete your programs such as gimp, google chat, drivers (including 3rd party), etc.?
4. When you do an upgrade, are your settings over written? Like the desktop background, program customizations, and other properties?

Upgrading is the supported method, although I never do anything bar clean install. Upgrading shouldn't affect your documents, but in any event, if data is valuable to you, you should not make the mistake of not having it backed up.

Upgrading will keep your applications in place, may well upgrade to newer versions, but your settings should remain the same.  


> Backup Questions:
1. What exactly can you backup? Like, can I backup my documents, programs, and settings?
*What is the home directory? What is it for? Are settings and program installations stored there or something?

You can backup as little or as much as you like, the home folder contains all your documents, files and settings.

---

### Post by daksai3 on 2010-08-17
Wow they weren't kidding when they said the people on the forums were good people. 

So what do you personally do when you do an upgrade?

Should i just put my home directory in another partition as a backup? I should just make a backup of my home directory right, as that contains all my documents settings? Is there anything else i have to backup? And for the upgrade im assuming that i should just do a fresh install with a disk as ive heard that using the upgrade manager sometimes leads to problems. 

but just one more thing. what about programs that you download? i assume that they dont go to the home directory, so do i have to install all my programs again, or is there an easier way?

and just how safe is it to use the upgrade manager?

---

### Post by howefield on 2010-08-17
> **daksai3 said:**
> So what do you personally do when you do an upgrade?

Me personally ?

As I said, I don't. I always choose the clean install route. That isn't to say I have anything against upgrading, it is a properly supported method, it is just that I prefer to start afresh when using a new version. I do the same with all operating systems.

> Should i just put my home directory in another partition as a backup?

It is a good move to have /home in a separate partition in any event, as it can make reinstalling the operating system easier, just mount the partitions but do not mark /home for formatting.

There are applications in the Ubuntu Software Centre that will help you back up /home.

sbackup and backintime to name a couple.

> I should just make a backup of my home directory right, as that contains all my documents settings?

Yep. As a minimum.

> Is there anything else i have to backup?

That's up to you, I like to keep an image of the disk, that way, whatever happens, a re-image is only a few minutes away. I keep all my documents/files/music/video/ect on a separate hard drive to the operating system with copies on a NAS and on external USB. 

> And for the upgrade im assuming that i should just do a fresh install with a disk as ive heard that using the upgrade manager sometimes leads to problems.

Well, yes, it can do, but I'd guess that most of the time there are no issues. Many people have upgraded all the way through from the first Ubuntu edition through to 10.04, it's not all that unusual.

I always fresh installed when using windows operating systems, so perhaps my thinking is clouded by that. I still fresh install, take all the updates/patches as they come due, and then fresh install when the next version comes out. 

> but just one more thing. what about programs that you download? i assume that they dont go to the home directory, so do i have to install all my programs again, or is there an easier way?

It is generally best, where possible, to take software from the official Ubuntu repositories. 

But sometimes you'll want something that isn't available from there, or perhaps the version in the repository has become "old" so you download it, let's take dropbox as an example, you'll download the .deb package from dropbox.com to your machine and run that package to install. If you then upgrade to the next version of Ubuntu, Dropbox will still be on your machine as it was. You won't need to reinstall it.  

> and just how safe is it to use the upgrade manager?

I have nothing bad to say about the upgrade manager, but perhaps users who use it more than me can answer it better.

---

### Post by Emperor_penguin on 2010-08-17
Hi there, im having questions abut install ubuntu too.:-s

Should i install the drivers from ATI before or after installing ubuntu? I mean, i use an ati 3850 series and in the Hardware Drivers tool, i can actually download the drivers, then reboot again into live cd and then install ubuntu. Or should just install with the open source drivers and after change to the ati drivers(catalyst included) for taking full power of my gpu?

thank to all.):P

---

### Post by howefield on 2010-08-17
> **Emperor_penguin said:**
> Should i install the drivers from ATI before or after installing ubuntu?

After installing Ubuntu.

---

### Post by daksai3 on 2010-08-17
If I place my home directory to another partition, am I copying it as a back up or permanently placing it there? Is there any diff, and is it possible for them to update each other, so that i dont have to periodically update it my self?


im new to this, so what do u mean when u make an image of ur disk? are u saying that u make it into an iso and then installing that as an operating system again if anything happens? pls clarify. 

so if i download things off the repositories, ubuntu will update them (if available) when i do the upgrade? and does this also apply if you do a clean install?


when you (in ur case) upgrade using a clean disk install, do u delete the previous version first and then install it? or does it just overwrite it?

and how do you keep ur previous settings? do u just copy and paste ur old "home directory stuff' into the new one?



ps. thanks for all the great help. ):P

---

### Post by oldfred on 2010-08-18
I have a newer hard drive with lots of room. So I have several 20-25GB / (root) partitions. One is my last install, one is my current install and another is the alpha/beta of the next install to see if it works on my system. I moved all my data into a /data partition and mount it in every install so all my data is the same. 

If just upgrading or a new install you can use the same /home. Or you can copy some or all of your /home settings over to a new install. /home should not be shared with other systems as settings & programs may be different versions and have conflicts.

I export a list of installed applications and include that in my backups of /home. I also try to copy into /home any special settings I make to the system that are in /etc. 


from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Full Disk install Lucid Graphical
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by daksai3 on 2010-08-19
Ok thanks, this thread has been a complete sucess for me, as it has answered all my install and upgrade questions. thanks. 

im considering this thread to be solved. and again, thanks.

---

