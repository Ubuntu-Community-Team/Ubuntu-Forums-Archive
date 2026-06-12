---
title: "Install/Boot from Live CD barely begins with a collision!"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Hesperion on 2008-05-01
Readying an HPa1025c with a 200 gb HDD and 1 gb of RAM. Windows XP all backed up and trimmed down. Plenty of disk space left. Did a defrag of the drive after removing crap and cleaning up. Getting set to do a dual-boot thing. I am very green so at this level I am pretty lost. My thinking was to get the Ubuntu booted from the DVD then go in the GParted to do the partitions adjustments and then go from there. Unfortunately didn’t get anywhere near that far.

Ran intergrity check on ISO disk that was downloaded earlier today (8.04); checked good.

Selected from dvd opening menu:
Run Ubuntu from live CD without changing anything on your computer

Held for a long time on the startup progress bar graphic then:
BLACK SCREEN with the following:

* Preparing restricted drivers…              [ OK ]
* Setting the system clock
* Starting basic networking…                 [ OK ]
* Starting kernel event manager…          [ OK ]
* Loading hardware drivers…
udevd-event [6549]: run_program: ‘/sbin/modprobe’ abnormal exit
udevd-event [7195]: run_program: ‘/sbin/modprobe’ abnormal exit
/etc/rcS.d/S10udev: 105: usplash_write: not found
/etc/rcS.d/S10udev: 105: /usr/bin/tput: not found
/etc/rcS.d/S10udev: 1: usplash_write: not found
/etc/init.d/rc: 317: usplash_write: not found
/etc/init.d/rc: 317: sed: not found
init: rcS main process (5947) killed by SEGV signal
init: Unable to execute “/bin/sh” for rc-default: No such file or directory
init: rc-default main process (7342) terminated with status 255

And that’s about it…

I loaded Ubuntu on my Eeepc with no really big problems. I have a feeling these are really big problems.

Is this enough information to give someone a clue? I can outline all the attached hardwar if that would help. If you could help me out it would be so great!

Thanks…:KS

---

### Post by BomberBongani on 2008-05-01
I am also having the exact problem, when rebooting after using wubi to Install. can someone please assist

---

### Post by dstew on 2008-05-01
It looks like a driver that was loaded caused the kernel to fail. The error messages don't say which module, they only record the consequences. Bomber, do you have the same computer as Hesperion?

To try to get Ubuntu installed in cases like this, you can try kernel parameters such as **noapic nolapic acpi=off** added to the kernel line by pressing F6 at the first menu. There are hundreds of kernel parameters, but those are the most commonly used I think. If you think it might be a graphics driver, you can try the parameter **vesa=force**, or see if there is a Safe Graphics Mode (press F6 for that too).

If the kernel parameters don't work, try installing using the Alternate Install CD. It uses a text-based interface that is more reliable. It may not load the driver that is causing trouble with the Live CD.

---

### Post by Hesperion on 2008-05-01
Dstew, could one enter those commands at the point where this code (above) stalls like you would at the cursor of the command line in a terminal? 

Just tried it again and got a string of:
/etc/init.d/rc: 317: sed: not found
Segmentation fault

(several times, then)

init: Unable to execute "/bin/sh" for re-default: No such file or directory
init: rc-default main process (7441) terminated with status 255

I will try to get into the safe graphics mode next.

---

### Post by Hesperion on 2008-05-01
Ok, no joy on adding in the commands to the kernel thingy at F6 went back and selected the safe graphics mode option. Very similar results. I did burn an alt CD so while I am waiting for some insights to get posted I will try and run that. Hope this looks familiar to someone out there. So far I have found nothing in the forums about this.

---

### Post by Hesperion on 2008-05-01
OK update: Ran the Alt CD and things went well to the point of the partitioning. Chose Guided: Resize Mater Partition and use freed space. Got:

for some unknown reason impossible to resize this partition
Check /var/log/syslog or see virtual console 4 for details.

Obviously, since I can't seem to make the Live CD run I do not have the luxury of the graphical UI in GParted. If there is some way to utilize that or something similar please let me know. I am shooting in the dark here. 

I decided to go back to XP and do some further clean up and re-defrag the drive. Hoping for the best.

Feel free to jump in here and give me you opinions. LOL

---

### Post by tanderson on 2008-05-01
Hopefully my symptoms are a result of the same problem and I am not hijacking or confusing this thread. I am running kubuntu and I upgraded from feisty through gutsy to hardy last week. Everything was good for a week and then I rebooted my machine last night and I ended up with the following error.

(about a whole page of the first line)
```
/etc/init.d/rc: 317: sed: permission denied
init: unable to execute "bin/sh" for rc-default: permission denied
init: rc-default main process (4708) terminated with status 255.
```

I booted live cd and found that bin/sh is a symlink to /bin/dash. /bin/dash had permissions of lrwxrwxrwx root root. So I think that is right?

googled and found this thread that talked about a problem in the fstab file. 

[URL="http://linux.derkeiler.com/Mailing-Lists/Debian/2004-04/4464.html"]

I though sweet!, because I had originally rebooted the machine because my 2nd hard drive mount was wrong and thought this must be the problem. I removed the "users" option according to the website but it didn't work for me.

In the error, is the 317 the line number in the script where the error occurred? I couldn't even tell you what language the script is but line 317 is "fi". which as far as I can tell would be a endif in basic and } in c/c++. I noticed that python was upgraded the other night and maybe this is a python parse error? I know! grasping at straws, but you know what they say about desperate people in desperate times.

---

### Post by Hesperion on 2008-05-02
I have made a decision. I am aborting this experiment for now. I realize that many factors have to come together in order to make what I want to accomplish happen. I know well the shortcomings of Microsoft's software and OS's. The dominance of their systems have created an environment in which manufacturers have (understandably) catered to them and their faulty operating system. They have become so preoccupied with attacks on their "swiss cheese" of an O/S that they have failed to make a good one to date. This is why drivers conflict and a whole host of problems ensue. It isn't Linux that has caused that situation it is MS and their combination of lazy only-game-in-town attitude and casual approach to programming and customer service as a result that is the trouble. The Linux interface developers have to deal with this and they have my fullest respect and admiration. 

Ubuntu, in my limited experience with it, has fully captured my attention but the learning curve is too great for me (at least this month due to committments) and will demand much more study and homework. I am not going to pursue my current dual boot installation project until I am more familiar with what is preventing it. [Presently I am looking at my screen at the partitioning stage of the installation from an alternate CD and do not feel competant to choose the option at this prompt. I want to preserve my trimmed down XP installation and successfully create a single system which has 2 usable operating systems on it.] Therefore I am going to do much more study and wait this thing out. 

I have a very successful working Ubuntu 8.04 system on my EeePc 4G Surf and I am very happy with it. It has holes in it but I know what they are. I am confident I will get them solved with the help of the community. I am not saying I have given up on Linux, Ubuntu or anything WE are trying to accomplish. I am just not prepared enough right now to get the job done in the hours I can presently spare. I will definately be monitoring these fora with interest to see how these issues develop.

---

### Post by olivine on 2008-05-02
> **Hesperion said:**
> [Presently I am looking at my screen at the partitioning stage of the installation from an alternate CD and do not feel competant to choose the option at this prompt. I want to preserve my trimmed down XP installation and successfully create a single system which has 2 usable operating systems on it.]

Hesperion,

If you're ready to try once more, my advice would be to partition using a GParted live CD, before running the alternate CD. You can download the live CD from the GParted website. I've run into problems several times at the partitioning stage using alternate Ubuntus (from Edgy on), while using GParted has so far always worked like a charm, including when shrinking windows system partitions (of course make a backup if it's important).

---

### Post by amitkr on 2009-06-27
I am not able to login to ubuntu 7.04. As the bootin starts and the bar starts filling, a black screen appears and it says - /etc/init.d/rc: 2: sed: Permission denied, almost 20 times. I tried to login from recovery mode, but failed. I don't have any clue now, how to recover my data. I got the ubuntu 7.04 live cd, somebody said run it, but it doesn't shows my data, so I am not installing it. Please, help me out.........plzzzzzzzzzzzz. My position is very bad and I despeately need my data. I don't have any backup of those. plzzzzzzzzzzzzzzzzz:(

---

### Post by presence1960 on 2009-06-27
> **dstew said:**
> If the kernel parameters don't work, try installing using the Alternate Install CD. It uses a text-based interface that is more reliable. It may not load the driver that is causing trouble with the Live CD.

+1

Sometimes the preferred method (Live CD) does not work. The alternate text based installer usually will. besides it gives way more installation options too. get it here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

just in case you want to play around before trying the alternate installer take a look here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

