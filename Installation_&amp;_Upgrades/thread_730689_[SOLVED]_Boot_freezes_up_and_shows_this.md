---
title: "[SOLVED] Boot freezes up and shows this"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by Streety on 2008-03-21
Ok I'm glad to say that thanks to the members of this forum, I'm using Linux right now and it's really nice. Shame it's at 800 x 600 and no effects. 

How do I install my Inno3D (nVidia) 8800GTS 512mb graphics card?

---

### Post by buntu_Geek on 2008-03-21
First of all i suggest you to check the CD for errors... 

Most of the cases .. ends up having an errorneous CD..

try another CD... check for the integrity of the ISO that you have before burning on to a disk ... is my next suggestion...

---

### Post by PmDematagoda on 2008-03-21
This is most likely an X-Server issue that can be linked to this:-
> 8800GTS

Boot Ubuntu in Recovery Mode and then install the nvidia-glx-new package using:-
```
sudo apt-get install nvidia-glx-new
```

After installation is done enable the Nvidia driver with:-
```
sudo nvidia-glx-config enable
```
after that is done, check your X-Server with:-
```
sudo startx
```

---

### Post by Streety on 2008-03-21
Thanks for the quick replies, I've checked the CD for errors and apparently there were none. So I'll try out that code thanks a lot :)

---

### Post by Mustard on 2008-03-21
> **Streety said:**
> Thanks for the quick replies, I've checked the CD for errors and apparently there were none. So I'll try out that code thanks a lot :)

I get the feeling the code above from PmDematagoda is for after you have installed, not during installation or the running of a live CD.  Maybe I'm wrong though.  The fact that he mentions 'booting into recovery mode' seems to indicate he has misread the opening post.

---

### Post by Mustard on 2008-03-21
What I would do is hit the relevant function key (F1 or F2 I think) at the very first screen when you boot the CD and look for some of the special boot options you can use to get the live CD started.

---

### Post by PmDematagoda on 2008-03-21
Woops, you are right, I missed that, sorry.

I am not sure if the code will work, but if it does not work then try booting Ubuntu in Safe Graphics mode.

---

### Post by fela on 2008-03-21
If your intending on installing it to your hard disk (not using it as a livecd), you could download and burn the 'alternate' install disk, and install it like that.

---

### Post by Streety on 2008-03-21
Ok so I'm back again and yes PmDetagoda your way does seem to be after Ubuntu is installed :P

I have something else, I want to keep XP and use them as dual boot. Would the alternate install disk let me choose where to install still so it doesn't wipe everything? Also what would I do about my Wireless card from D-Link to get it working in Ubuntu?

Attempting to boot it again so I'll be back in a min :)

---

### Post by Mustard on 2008-03-21
> **Streety said:**
> Ok so I'm back again and yes PmDetagoda your way does seem to be after Ubuntu is installed :P

I have something else, I want to keep XP and use them as dual boot. Would the alternate install disk let me choose where to install still so it doesn't wipe everything?

The Alternate CD installation gives all the same options for installing that you get from installing from the live CD.  It just not as pretty.

Personally I'm more familiar with the alternate installation methods than the live cd install, as the alternate installation was all we had when I first started using Ubuntu. :)

The advantages you would get from using the live CD, I think, would be the ability to partition the drive before you start the installation, using the GParted software.  I assume its on the live CD anyway.  GParted is a graphical partitioner, so its a litte bit more intuitive to use.

---

### Post by Streety on 2008-03-21
Ok I'm downloading the alternate CD. I already have a partition that is in Ext3 format for Linux so I should just be able to choose that right?

---

### Post by PmDematagoda on 2008-03-21
Yes, I do not think you would have much of a problem with the Alternate CD since, even though it is only text, the instructions are given clearly.

---

### Post by Mustard on 2008-03-21
> **Streety said:**
> Ok I'm downloading the alternate CD. I already have a partition that is in Ext3 format for Linux so I should just be able to choose that right?

The simple answer is yes. :)  

You may however divide that partition up even further, if possible, at a latter stage.  The basics you will need are a partition formatted in ext3 and a very small partition formatted for a swap drive.  The install CD should allow you to do this, if you tell it to use that ext3  partition.  It should then break it up into a ext3 partition and a small swap drive partition.

Ideally, you would break it up into 3 partitions,  One to be used for the / root directory (the equivalent of the system files in windows), one for a swap drive (the equivalent of the swap file in window), and one for the /home directory (the equivalent of the My Documents folder in windows).  The advantage of having a separate /home partition, is that you can reinstall the operating system from scratch while retaining your personal settings and data.

Initially I would go with the straight install, then before getting to carried away installing programs and setting up personal configurations, I would read up on some stuff about setting up a /home partition, and then dive back into the partitioning and installation process again.  Practice makes perfect..hehe..and I've borked enough installs to have had lots of practice. :)

---

### Post by Streety on 2008-03-21
Ok guys downloaded the CD, burned it and now I am going to attempt to boot, wish me luck! ;)

---

### Post by Mustard on 2008-03-21
Good luck!

I'm off to bed.  I'll be looking for your progress in the morning. :)

---

### Post by Streety on 2008-03-21
Well I got somewhere! :D It's installed yet what Dematagoda said earlier about booting into recovery mode didn't work, it said something about not being able to find my monitor. I use a Samsung Syncmaster 932B monitor and, like I said earlier, an Inno3D 8800GTS 512mb. The maximum resolution I was allowed in Ubuntu was 800 x 600 where I can have up to 1280 x 1024, once this problem is sorted it's just my wireless then I'm good to go!!

---

### Post by PmDematagoda on 2008-03-21
Did you install the nvidia-glx-new package? Are the problems you described those that you got after installing and configuring the package?

---

### Post by Streety on 2008-03-21
Well I was in Ubuntu and the screen was huge at 800 x 600 so I restarted, went into recovery mode like you suggested and then did what you said. Yet they did not work. I can take a picture of what came up if you want? As I'm not fluent in Ubuntu computer terminal and stuff (want to learn it :) ). So should I get a picture?

---

### Post by PmDematagoda on 2008-03-21
There is no need for a picture.

Just do this:-

1) Boot Ubuntu in Recovery Mode.

2) Remove the nvidia-glx-new package with:-
```
apt-get remove --purge nvidia-glx-new
```

3) Download the Nvidia driver:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
```

4) Run the driver:-
```
sh NVIDIA-Linux-x86-169.12-pkg1.run
```

5) Reconfigure the X-Server after installation:-
```
dpkg-reconfigure xsever-xorg
```

6) Start the X-Server with:-
```
startx
```

---

### Post by Streety on 2008-03-21
Ok that's great, just one problem. I'm far from my router so I use wireless. How would I go about getting my D-Link AirPlus G DWL-G510 wireless card to work in linux?

---

### Post by PmDematagoda on 2008-03-21
Hmm, that is a bit of a problem, but how did you manage to install the nvidia-glx-new package?

---

### Post by Streety on 2008-03-21
It was on the CD. Also Linux works very well with my wireless card so I'm using it right now :) 

Still having problems with the graphics card though, says that URL you gave doesn't exist. What if I got the UK (where I'm from) Driver for my card from the site and just used straight from regular ubuntu. How do you install on this anyway? :D

---

### Post by Streety on 2008-03-21
Oops double clicked reply there, sorry :\

---

### Post by Streety on 2008-03-21
YES IT'S WORKING

Everything is working fine now :D now to get my head around using the terminal etc heh.

Thanks for all the help guys :)

---

### Post by Mustard on 2008-03-21
> **Streety said:**
> YES IT'S WORKING

Everything is working fine now :D now to get my head around using the terminal etc heh.

Thanks for all the help guys :)

Well done. :)

---

### Post by buntu_Geek on 2008-03-21
Hey,
Don't forget to mark the thread solved dude...

See in the thread tools option at the top of your thread....

---

