---
title: "HPLIP 3.9.12 Installation"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by bwsmith25 on 2010-02-10
Can someone PLEASE help me? I have been trying for the last week to install drivers for my HP F2480 printer. I cannot get anything to install and cannot seem to find anyone to help me.

I am new to Ubuntu (used Windows all my life until I finally got tired of it) so I don't know that much about it - but I do know what my version (Karmic) comes with HPLIP 3.9.8 and my printer must have at least HPLIP 3.9.10 to work.

How do I install the updated HPLIP? And please don't send me to [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html), because I've tried doing the install repeatedly and it keeps telling me I have missing dependencies and I don't know where to get them or how to install them.

Someone, please help me - I am at a breaking point here - I have to have a printer and I don't want to buy another one. (I bought the HP because my Dell printer doesn't work with Linux and I've read that HP's are good with Linux - but I guess I bought the wrong one.)

---

### Post by skogs on 2010-02-10
Hold on there buddy.  I'm about to install it myself.  I'll let you know what I come up with.

---

### Post by skogs on 2010-02-10
I don't know what to say to help you man.  I did in fact click on that link you posted, and downloaded direct from HP's sourceforge page.  

It downloaded and installed just fine with the 'a' for automatic settings.  I happened to pull down a crap ton of developer dependencies, which I could have probably done without.  They were either working on the bleeding edge, or just didn't know how to build their application with non-dev tools.  Overall pretty slick though.

The only option that you might be having trouble with is the repositories.  All those non-standard install things come off the repos, and if you don't have them enabled, then they won't work when aptitude tries to install them.

Check the [Repo management page]("https://help.ubuntu.com/community/Repositories/Ubuntu") -- follow the pretty pictures to enable all the repos.

If that doesn't allow the install script to continue on unabated, then post the last few lines here so the guys that are smarter than I am can help you.

---

### Post by SaintDanBert on 2010-02-10
I am running HPLIP v3.9.12 on Ubuntu Karmic, but I had to download and install and build. I may be able to answer specific questions.

I have an HP OfficeJet-8500 Premier that is wifi connected to my home LAN. It prints and scans under both linux and win-dose control with very little trouble. On spot-of-bother revolves around the printer "connection" with linux. 

When the computer leaves the LAN to go walkabout, naturally the printer connection breaks. When the computer returns to the LAN, one must kick-the-can before the connection wakes up. You try to print something and cups complains that the printer is not connected. Sometimes the printer wakes when you queue a fresh job. Sometimes the commands **cupsdisable ...** and **cupsenable ...** will wake things. 

I don't have a smoking gun, but troubles seem related to jobs on queue when the connection breaks or queued while the printer is not connected while walkabout.

---

### Post by bwsmith25 on 2010-02-10
Okay, I just tried the HPLIP install again. I get the same errors I always get. 

Here is a screenshot:

[ATTACH]146714[/ATTACH]

Where do I find these dependencies? Every time I try to install them it says error - what am I doing wrong?

---

### Post by sgosnell on 2010-02-10
As I told you in another thread, you need to enable the proper repositories.  Did you read the link that skogs posted above?

---

### Post by bwsmith25 on 2010-02-10
Does anyone know if Ubuntu 10.4 will come with HPLIP 3.9.10+?

If so I can just wait it out until the new version comes out - I was going to upgrade to the LTS anyway.

I'm just too tired and frustrated with trying over and over and over to get this to work - so tired in fact that I've thought about going back to Windows (as much as I would hate to do it) but I can't use an OS if I can't have my printer - it defeats the purpose of having it if everything doesn't work with it properly.

---

### Post by sgosnell on 2010-02-10
Ubuntu does not come with HPLIP.  You have to install it, whatever the version.  Set up the repositories properly, and you can install it easily enough.  I installed 3.9.12 without any problems, but you don't need HPLIP to print, just to use the extra features, like tracking ink levels, etc.

---

### Post by bwsmith25 on 2010-02-11
Yes I enabled the repositories. It still doesn't install and my printer still doesn't print. I tried plugging in the printer and printing before I tried installing HLIP - and nothing I have tried thus far has worked.

---

### Post by bwsmith25 on 2010-02-11
> **sgosnell said:**
> As I told you in another thread, you need to enable the proper repositories.  Did you read the link that skogs posted above?

I read the link, and as far as I know I have enabled all the repositories. But, I still get the same errors when trying to install HPLIP's dependencies. 

I honestly have no clue what I'm doing - I'm new to Ubuntu.

If I provide screenshots of what I'm doing step by step, can someone please help me figure this out? I really don't know what to do or how to do much of anything in Ubuntu yet. I thought that plugging in the printer would be sufficient to get it to print, but it wasn't.

---

### Post by finlost on 2010-02-13
A screenshot of your repositories might be most beneficial at this point.

---

### Post by bwsmith25 on 2010-02-16
Okay, I finally installed HPLIP 3.9.12 - stupid me couldn't see one setting that had to be changed in my repositories.

Now, my printer is recognized, but it won't print when I try to print a document, and when I attempt to print a test page it shoots out a blank page.

Any ideas on what the next phase is to get the printer up and running?

---

### Post by sgosnell on 2010-02-18
Are you certain you installed the proper driver?  It's possible to click and set the wrong model by accident.

---

### Post by bwsmith25 on 2010-02-18
> **sgosnell said:**
> Are you certain you installed the proper driver?  It's possible to click and set the wrong model by accident.

I thought I did, but I could have clicked the wrong one by accident. I will check that out when I get home today and reply once I know for certain.

---

### Post by bwsmith25 on 2010-02-19
You were right - I installed the wrong driver by mistake. My printer is now up and running.

THANK YOU to everyone for all the help.

---

### Post by desertfox3 on 2010-04-14
travis@travis-desktop:~$ sh hplip-3.10.2.run
sh: Can't open hplip-3.10.2.run
travis@travis-desktop:~$ 

i did what the hp linux website said and i get nothing....what am i doing wrong?

---

### Post by sgosnell on 2010-04-15
You need to set the executable bit on the file, then make sure you're in the directory with the .run file and enter ```
./hplip-3.10.2.run
```Or you can do it all from Nautilus, by right-clicking on the file, selecting Properties, and checking the box for "Allow running the file as an executable" or words to that effect.  I'm at work right now, on a Windows box, no access to a Linux machine.  Then double-click the file, or right-click and select Run.  Choose to run it in a terminal when prompted.  That should do it.

---

