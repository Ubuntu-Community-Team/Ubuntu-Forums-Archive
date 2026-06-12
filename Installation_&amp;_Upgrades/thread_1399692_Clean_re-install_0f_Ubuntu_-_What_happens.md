---
title: "Clean re-install 0f Ubuntu - What happens?"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by boosterjet on 2010-02-06
Hi, a little self inflicted injury. I have a two hard drive set up one a 160gb with Win XP and the other with a 80 GB with Ubuntu. Both were working perfectly after a bit of tweaking earlier, then I did a silly thing - saw in Places menu an entry called 160GB file system. Opened it and it was full of Window files, none of which could be opened by Ubuntu's file manager, so I deleted the lot !!. This deleted all my Win XP operating system. Had to call in a techie to reinstall Win XP, the whole sorry saga , if interested here [http://ubuntuforums.org/showthread.php?t=1396336](http://ubuntuforums.org/showthread.php?t=1396336). Well Windows is now up and running after a lot of work updating, reloading applications,( lost my favourites list) fortunately had all my important stuff backed up. I want to get back to Ubuntu, what happens if I do a complete re-install? Will I lose all the set up work done to get Grub2 installed and the grub menu working properly and recognising the Windows drive, or will that all have to be redone. Not too worried if I have to but it will be a bit of a bloody nuisance if I do. Fortunately I had great help previously on my first set up (thanks again Kansasnoob) and can reference all that again if needed.

---

### Post by mushwars on 2010-02-06
I am so sorry for your loss. :cry:

If you somehow ruined your ubuntu then have  no fear, that is the nice thing about linux, it is durable, you can take an axe to it and get it working again. We will be here every step of the way for you even if you do have to reinstall. 

Just wanted to let you know that the live cd is an excellent resource.

You can chroot into your system from the live cd just as if you were in it and paste us error logs, etc. If there are missing/broken files, you can essentially take them from the live cd and copy them to the right directories. 

I was working on my brothers kubuntu with my gentoo live cd, and ofc thats a bad idea because it overwrote some of his files with gentoo binarys which are not compatible, all I had to do was chroot from his cd and copy over the right files, and it worked again.

---

### Post by boosterjet on 2010-02-06
Ok, I have started the re-install twice and have been forced to quit both times, all goes normally until the keyboard selection page. When I hit forward the disc partioner starts and takes me to the prepare disc space page where I am supposed to get a "guided-use entire disc button". All I get is a reading saying that Windows is already installed on 160gb and wants me to partition it for installation. On my original install I got the guided button and was given the choice of my 160 or 80gb drives for installation, not now. I have no intention of partitioning so I hit quit which quits me to a Ubuntu Home Page where I can access my 79gb file system through Places. I then have to close down from the ubuntu prompt in the top right corner of the top tool bar. Obviously not detecting my 80gb drive during install. Checked my bios, start order is cdrom,cdrom then hard drive. CMOS gives the hard drive boot order as 160drive as first boot priority then 80gb as second. Should I change this to the 80gb as first boot priority. I am not sure about playing about with this area. I sure don't want to lose Windows again or stuff up the whole thing. Techies are expensive!!

---

### Post by boosterjet on 2010-02-06
Just tried it, ie, changing hard disc priority, no different, the amazing thing is when I start re-install a page comes up in the initial loading sequence that shows it has detected a previous  karmic koala program but goes through a lot of purging. When I quit from the "prepare disc" page I get returned to this Ubuntu home page which is obviously the trial page but it has an install Ubuntu icon mounted. Looking at its properties it says it will install to my hard drive. No way. Open up Places and as I said before there is a 79gb file system "place". Opened it and all my files , home page, music etc, are all still there. Just will not recognise the 79gb drive. Bios recognise both. What now ??

---

### Post by mushwars on 2010-02-07
I REALLY want to help you but I didnt sleep last night because I have been on these fourms for the past 24 hours answering questions. I need to sleep.

Dont give up hope. Someone will answer you, I hope.

( I am what you would call addicted to helping people and I cant stop, I help someone resolve there problem and in the meantime am helping several others, I just want to see their problems through to the end. I have to stop now, I am sorry that you never got your answer. )

---

### Post by exploitations on 2010-02-07
I kinda understand whats happening here (just quickly read over everything)
I've installed Ubuntu about a million times, so I know how the installer thingy works.

Theres usually 3 options, one to select a certain disk space for ubuntu and windows, to use the entire disk, and the third option is advanced something of such. Select the third one, and you should see all the partitions on your drive. (that is if you're using only one hard drive)

Hope this helps.

---

### Post by boosterjet on 2010-02-07
Many thanks to all for all their time but I did it. Researched everything and finally found a help page in Ubuntu community forums "RecoveringUbuntuAfterInstallingWindows". Not being all that computer savvy I proceeded with caution and Voila! all back to normal. Happy days are here again!

---

