---
title: "Upgrading to 64bit"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by alanrlow on 2010-06-28
I have been running Ubuntu on an old Acer Aspire laptop for several  years without a glitch and recently upgraded to a newer core two duo  laptop.
I cloned the HD from the old to the new laptop without a problem,  despite being told it wouldn't work, (he only knew windoze) 
The thing is now that I have a 64bit processor I would like to[COLOR=blue][COLOR=blue ! important][FONT=Verdana] [COLOR=#000000]upgrade[/COLOR][COLOR=blue ! important][FONT=Verdana][/FONT][/COLOR][/FONT][/COLOR][/COLOR] to the 64bit version  of  Ubuntu, (without losing my data of course)
My new system is an, Acer TravelMate 6410 with 160gb SATA HD setup as:
 
SDA1  20gb ROOT
SDA3  45gb extended partition
SDA5  45gb home partition in the extended partition
SDA4  5gb swap
SDA2  80gb partition for other stuff.

I am thinking that if I do  an install but don't format the home partition (SDA5) everything should  be OK. 
My only other concern is setting up all the programs I have  now, like VirtualBox, all my Wine programs, all the extra games etc I  have installed. Could I create an APTonCD disk and put it back that way?
 
Any advice greatly appreciated.
Regards,
[COLOR=#888888]Alan.[/COLOR]

---

### Post by robsoles on 2010-06-28
Hi alanrlow,

I have been running 64 bit (AMD64) for a while, on an intel atom n450 based lappie, and there are a couple of things that are slightly more painful but overall it is f'n brilliant!!!

Just be careful that you don't mark the partition you have been using for '/home' for formatting as you install and it should be fine - you'll need to cope with manual partitioning but to have a seperate '/home' partition you or someone you know already coped with that once anyway!!!!

Ask more questions if you are still unsure till you are sure and then bite that bullet and commit - 2nd worst case scenario is that you end up reinstalling the 32 bit version of Ubuntu instead!


My edit: Worst case scenario is you fall asleep at bad point in install process and format that '/home' partition!!!     Grievous boss is on my installation of AMD64 on his work desktop and home laptop PCs, Cool engineer (also at work) is on my install of AMD64 on his work desktop, server machine at work is using i386 ubuntu. Server at home is AMD64, desktop at home is AMD64 - there are more but I already feel a bit like I am gloating so I will stop!!!

---

### Post by warfacegod on 2010-06-28
You'll need to remember to mark your Home partition as /home. As long as you don't format it, you'll be fine.

> Could I create an APTonCD disk and put it back that way?

I don't think this will carry over very well from 32 to 64. Your best bet is to simply make list of everything you want to reinstall. Because you have a separate /home partition most/all of the settings you have for these apps will carry over to your new account. Be forewarned though. You may have issues with settings compatibility going from 32 to 64 bit versions of your apps.

---

### Post by alanrlow on 2010-06-28
> **robsoles said:**
> Hi alanrlow,

I have been running 64 bit (AMD64) for a while, on an intel atom n450 based lappie, and there are a couple of things that are slightly more painful but overall it is f'n brilliant!!!

Just be careful that you don't mark the partition you have been using for '/home' for formatting as you install and it should be fine - you'll need to cope with manual partitioning but to have a seperate '/home' partition you or someone you know already coped with that once anyway!!!!

Ask more questions if you are still unsure till you are sure and then bite that bullet and commit - 2nd worst case scenario is that you end up reinstalling the 32 bit version of Ubuntu instead!

Thanks for the reassurances.
What are the slightly more painful things about 64bit version?

Yes I did set up the separate partitions but it was a year or so ago and I haven't had to fiddle with it since so I hope memory doesn't fail me. ;p

---

### Post by warfacegod on 2010-06-28
> Yes I did set up the separate partitions but it was a year or so ago and I haven't had to fiddle with it since so I hope memory doesn't fail me. ;p

The OS partition will be / and Home is /home. Pretty straight forward.

---

### Post by robsoles on 2010-06-28
The major pain I can think of right now was Flash - I had to make flash (ie, adobe crap) work properly in each graphical install of AMD64, it wasn't an issue in my text only setup. There is post after post and method after method of doing it, I kept looking till I found a method with very few steps indeed.

There is something else but it is so minor that I just can't dredge it up right now - Googling something like 'problems running 64 bit Ubuntu' will probably turn it up but seriously don't worry about that.

(I just re-read your OP with a clearer head!)
Um, your wine and virtualbox 'stuff' is all stored in your home directory so you've an excellent chance that just a few minutes using 'ubuntu software centre' will quite possible restore your stuff. I prefer the non OSE version of virtual box directly from [www.virtualbox.org](www.virtualbox.org) and will happily post on how to follow their instructions if they aren't clear enough for you.


Have you got a second system you can access forums with if you can't remember what to do at 'manual partitioning' step on the machine you are upgrading to 64 bit?

---

### Post by warfacegod on 2010-06-28
> Have you got a second system you can access forums with if you can't remember what to do at 'manual partitioning' step on the machine you are upgrading to 64 bit?

When a Live Environment is in use, all that is needed is to open Firefox. Preferably on a different Workspace.

---

### Post by robsoles on 2010-06-28
> **warfacegod said:**
> When a Live Environment is in use, all that is needed is to open Firefox. Preferably on a different Workspace.

LOL, yup - I always forget the desktop remains accessible if you choose 'try ubuntu' and then double click the 'install ubuntu' icon given on the desktop once it loads.

Make sure you choose 'try ubuntu ...' at first menu off 10.04 LTS Desktop AMD64 CD and then double click the install button on the ensuing desktop and you should easily have internet access in a browser all the way through the installation process (though I haven't tested it!)

---

### Post by warfacegod on 2010-06-28
> (though I haven't tested it!)

I have. Things tend to get very sluggish during the actual install process especially if a LiveCD is used instead of LiveUSB and depending on how much RAM is in the computer, but the Internet works straight through the entire process.

---

### Post by alanrlow on 2010-06-28
> **robsoles said:**
> The major pain I can think of right now was Flash - I had to make flash (ie, adobe crap) work properly in each graphical install of AMD64, it wasn't an issue in my text only setup. There is post after post and method after method of doing it, I kept looking till I found a method with very few steps indeed.

There is something else but it is so minor that I just can't dredge it up right now - Googling something like 'problems running 64 bit Ubuntu' will probably turn it up but seriously don't worry about that.

(I just re-read your OP with a clearer head!)
Um, your wine and virtualbox 'stuff' is all stored in your home directory so you've an excellent chance that just a few minutes using 'ubuntu software centre' will quite possible restore your stuff. I prefer the non OSE version of virtual box directly from [www.virtualbox.org]("http://www.virtualbox.org") and will happily post on how to follow their instructions if they aren't clear enough for you.


Have you got a second system you can access forums with if you can't remember what to do at 'manual partitioning' step on the machine you are upgrading to 64 bit?

Yes I have a second machine so should be OK.  

What in your opinion is the difference between the two Virtualbox's? I have always used the OSE and had no problems but am always willing to learn. 

As soon as the new disk arrives I'm ready to take the plunge, should be this weekend.
Thanks everyone for the help/ assurances.

---

### Post by robsoles on 2010-06-28
> **alanrlow said:**
> ...

What in your opinion is the difference between the two Virtualbox's? I have always used the OSE and had no problems but am always willing to learn. 

...

At the obvious end it is easier to get USB devices to work with the closed source version and at the slightly less obvious end the latest full release version of anything usually has some serious benefits though sometimes that theory falls right on it's backside where something comes unstuck because you use some feature of the software that the developer(s) just didn't check after changing code that influences it.

Oh, another benefit is that you can use the 'remote display' feature although I usually use something 'natural' to my client, ie RDP in Windows and VNC in Linux. 


In switching over I found that my old VMs started up fine under it (I mean there was no re-writing or jigging them required), I have found out since that it was a good thing they were 'off' and not 'saved' because it would have been painful had they been saved (apparently). It can be installed using 'apt-get' and updates are released by Oracle at mostly a reasonable rate.

I recommend it because my VMs seem a little more responsive (start up etc etc) using it.

---

### Post by alanrlow on 2010-06-29
> **robsoles said:**
> At the obvious end it is easier to get USB devices to work with the closed source version and at the slightly less obvious end the latest full release version of anything usually has some serious benefits though sometimes that theory falls right on it's backside where something comes unstuck because you use some feature of the software that the developer(s) just didn't check after changing code that influences it.

Oh, another benefit is that you can use the 'remote display' feature although I usually use something 'natural' to my client, ie RDP in Windows and VNC in Linux. 


In switching over I found that my old VMs started up fine under it (I mean there was no re-writing or jigging them required), I have found out since that it was a good thing they were 'off' and not 'saved' because it would have been painful had they been saved (apparently). It can be installed using 'apt-get' and updates are released by Oracle at mostly a reasonable rate.

I recommend it because my VMs seem a little more responsive (start up etc etc) using it.

Thanks for the reply. Something more to consider, although for the few times that I do use VB it's not high on the list of to-dos. 
Thank you for your help and I'll yell if I have any problems.

---

