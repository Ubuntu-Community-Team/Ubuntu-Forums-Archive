---
title: "Can't create persistent live usb of 11.04"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by EdwardR on 2011-04-01
Hi all,

I want to play around with xubuntu 11.04 Beta1.  I have tried to create a persistent live usb thumb drive using Startup Disk Creator, but have not had any luck.  I have tried running Startup Disk Creator from Linux Mint 9 xfce (currently installed on my machine) as well as from live sessions of ubuntu 11.04 Beta1 and xubuntu 11.04 Beta1.  When using Startup Disk Creator in Linux Mint, I am able to set the slider to choose how much reserved space I want, but when I reboot, the USB stick does not load, I get an error message about an unknown name in the file.  When using the live sessions of ubuntu or xubuntu, the section with the slider to choose how much of the usb stick to devote to the persistence file is greyed out.  I get the same result whether I choose the xubuntu iso or the ubuntu iso as the source disc image. I have used the same USB stick and Startup Disk Creator to make persistent live installs before - is there something about 11.04 that does not allow persistence?

thanks

Ed

---

### Post by ronparent on 2011-04-01
Have you tried using the utility 'testisk'? It is designed to work with the developmental release, in this case currently 11.04 and syncs with the daily image and allows designating reserved space. It is installed from the Ubuntu Software Center. I currently use it to test and install to test partitions.

---

### Post by EdwardR on 2011-04-01
Sorry ronparent, I can't find testisk in the software center or synaptic.  There is a program called testdisk, but the description doesn't look like it. 

<edit>  looking some more, I found testdrive, I'll install that and see how it works.

---

### Post by ronparent on 2011-04-01
It is testdrive (My wayward fingers, memory slips and small type cross me up all the time). Do try it.

ps: I can't believe that no ones bugged you yet about posting on 11.04 here.

---

### Post by EdwardR on 2011-04-03
Arrgh, it didn't work.  The version of testdrive that is in the Mint 9 repositories is an earlier, command line version and it did not seem to have an option to install to USB.  I could run a live USB of xubuntu or ubuntu 11.04 and then install the current version of testdrive, but I didn't think I have enough memory to then download the xubuntu iso in order to use testdrive to create a persistent USB.  So I figured I would have to install 11.04 to a computer in order to use testdrive to create a persistent live USB.  But I didn't have a spare partition to install it to, so I swapped hard drives with an old drive, installed xubuntu 11.04 beta 1, then installed testdrive, downoaded the iso, and guess what?  When using testdrive to create a live USB, the option for reserving space for persistence is greyed out, just like when using Startup disk creator!  All that work and it still didn't work.

Any other ideas to make a persistent USB of xubuntu 11.04?

ps.  ronparent, what did you mean about getting bugged about posting about 11.04 here?

---

### Post by ronparent on 2011-04-03
With 11.04 referenced in the title a forum moderator usually informs you that you should be posting in the Development & Programming section of these forums (displaying the Mint logo doesn't help either) and moves it there. 

Testdrive is also available in 10.10 (also the Mint version if the fancy strikes me). I use a 4Gb stick with 1Gb of reserved space. Is it possible that yours is a 2Gb stick?

---

### Post by EdwardR on 2011-04-03
OK, I see.

It's actually a 1 GB stick, but I have used it before for persistent installs.  I'm able to install install wireless drivers and remember my network password and browser bookmarks.  I just don't try to install a bunch of programs and it has always worked before.

---

### Post by ronparent on 2011-04-03
11.04 currently would just about fill a 1Gb stick. Once slimmed down for final release it will probably fit a cd.

---

### Post by Dutch70 on 2011-04-03
> **ronparent said:**
> With 11.04 referenced in the title a forum moderator usually informs you that you should be posting in the Development & Programming section of these forums (displaying the Mint logo doesn't help either) and moves it there. 

Yeah...lol

If the title said Can't create persistent live usb in 11.04, this would have been moved by now. 

He's actually (presumed to be) using a stable release though, so it's no different than asking about creating a bootable usb stick with any other distro.

---

### Post by EdwardR on 2011-04-04
I thought this was an appropriate forum since I viewed my question as an installation question.  I'll be happy if it is moved, just so long as I get an answer.

It installs to my 1 GB USB (without persistence) leaving 275 MB to spare, which is about typical for the distros I have tried that fit on a cd (my 1 GB USB stick is actually a little less than 1 GB available).  I have created persistent installs to this same stick with other ubuntu-based distros, he nce my curiosity as to why this one is not working.  I think I'll download 10.10 just for grins and see if that one works.

---

### Post by Dutch70 on 2011-04-04
How much extra space do you need it to have? I've had the same problem when trying to use all of the remaining disk space for persistence, but if I shortened it a little, it worked. You may want to give that a shot.

---

### Post by EdwardR on 2011-04-06
Well, I got my hands on a 2 GB thumb drive and tried again, and this time the persistence option in Startup Disk Creator was available and not greyed out, so maybe Ubuntu's version of Startup Disk Creator has some minimum threshold size for the thumb drive before it allows for a persistent live install?  So I installed it and the persistence worked, hooray!  But then I installed the wireless driver but couldn't see any wireless networks, boo hoo.  But that's not a problem for this thread.  I'll go ahead and mark the thread solved since I got persistence to work with a larger thumb drive.

---

### Post by lpd on 2011-05-01
Well, I can say that it doesn't work for me either. I have a partitioned 4GB flash with 1,5Gb reserved for Ubuntu. 11.04 wont let me reserve space for files and such. However 10.10 will.

---

### Post by joseph2221 on 2011-05-02
is there a way to create a copy from the 11.04 in my system?

---

