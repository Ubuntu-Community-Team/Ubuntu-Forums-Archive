---
title: "Polling for 10.04 Experiences"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by coffee412 on 2010-09-15
Recently used 10.04 for a install on a customers system. I think I made a mistake but I want to get an accurate idea of what others think. 

I installed the 32bit version on a 2 year old HP tower. Here is what I experienced and just want to know if others had the same types of problems:

1. Installation went fine. But on first boot I could not get past the login as I was caught in a loop. Login --> try to load desktop ---> back to login screen. Found out it was a video card problem. Customer had a sis chrome blah blah cheap card. Replaced with older Nvidia (6100?) and that solved that problem.

2. Created a secondary account for wife. On logging in to secondary account could only get desktop background image. No Panels on top or bottom showed. Could right click and thats it. Tried several times more (del account / create account) and same problem. Sometimes the desktop panels would appear but most times nothing but background image. Could right click with mouse but thats not much help.

3. When computer went into sleep mode, Recovering corrupted the video and crashed system. I understand this might be a swap problem but have not had a chance to look it over.

4. Perhaps Im nit picky, But different user accounts appartantly cannot share the same external drive for backup purposes? On installation, 10.4 gave main account ownership rights. Prevents 2nd account from using drive. Drive doesnt even show up for 2nd account. Have to play with permissions I guess.

I choose Ubuntu for customers because 9.10 worked so well on a few systems. I really like the Ubuntu center for installing software. I think its fantastic as I come from Fedora land and its kinda awkward there for most customers to install software. 

What do you think? 10.04 released too soon? Too buggy to use? Should I revert to 9.10 (EOL soon isnt it?) for customers or should I investigate mint?

What is your overall judgement of 10.04? Inquiring minds want to know! ;)

- This is not a rant. Just need to get an accurate idea from others.

coffee412

---

### Post by wkulecz on 2010-09-15
Overall my 10.04 experience has been positive, a few too many changes that serve no real purpose other than to make things different, but none of the Pulse Audio problems I had with 8.04.  

Perhaps a few more mysterious annoyances like the volume control disappearing from the the Gnome menubar and the cups PDF printer driver just disappearing after a reboot.  Both these were on my wife's computer so its possible it was something she did, but she is not one to click around to see what will happen.  Also some issues with CD/DVD burning that appear to have been fixed by a recent update.

Overall I wouldn't go back to any other version over 10.04, but I'd still rate 6.06 as setting the standard for quality on initial install.

I would be a lot less happy if I haddn't had my first (bad) experiences with grub2 on a throwaway 9.10 system first.

Maybe the LTS releases hould be moved back a couple of months to be xx.06 instead of xx.04, certainly both 8.04 and 10.04 were pretty solid by July/August after their release.

---

### Post by mörgæs on 2010-09-15
This forum might be more on-topic:
[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

9.10 is supported until april 2011, so there is plenty of time left for that one. The regular releases always have a year and a half support.

---

### Post by mörgæs on 2010-09-15
> **wkulecz said:**
> 
Maybe the LTS releases hould be moved back a couple of months to be xx.06 instead of xx.04, certainly both 8.04 and 10.04 were pretty solid by July/August after their release.

This applies to Ubuntu in general, not only LTS. For a beginner I would not recommend a brand-new version unless the older ones have been proven guilty.

---

### Post by malspa on 2010-09-15
Great experience with Lucid here.  Best LTS to date.

> **wkulecz said:**
> Maybe the LTS releases hould be moved back a couple of months to be xx.06 instead of xx.04, certainly both 8.04 and 10.04 were pretty solid by July/August after their release.

Generally, I think it's a good idea to wait a couple of months before installing a new LTS release.

---

### Post by jimbo99 on 2010-09-15
Even if the machine were a couple weeks old, if you had problems like this, you should check the hardware.  Test the HDD and RAM primarily.

I rarely advise people to enable power management in any OS.

Were you successful at operating the computer using the Live CD?

Were you dual booting?  Did you do a wubi install?

Test the HDD with gsmartcontrol.  The most current ISOs of Ubuntu no longer have the RAM test program.  You can still download an ISO for just that purpose so all is not lost.  I think the program is called memtest86.

Unless you know for certain because you tested the hardware you could be chasing your tail.  I'd recommend testing your hardware first then correct any problems and then try again.

---

### Post by melipone on 2010-09-15
I just installed Lucid Lynx on my main machine at work a couple of days ago. I had some problems with certain packages during installation (ipopd and nvidia-glx-new). The closing of the installation was messy. I filled out bug reports about those problems and I restarted the machine myself.  So far, so good. 

My rant so far is the renaming of dos2unix to fromdos (and unix2dos to todos). Why renaming of those classics necessary?

---

### Post by coffee412 on 2010-09-15
> **jimbo99 said:**
> Even if the machine were a couple weeks old, if you had problems like this, you should check the hardware.  Test the HDD and RAM primarily.

I rarely advise people to enable power management in any OS.

Were you successful at operating the computer using the Live CD?

Were you dual booting?  Did you do a wubi install?

Test the HDD with gsmartcontrol.  The most current ISOs of Ubuntu no longer have the RAM test program.  You can still download an ISO for just that purpose so all is not lost.  I think the program is called memtest86.

Unless you know for certain because you tested the hardware you could be chasing your tail.  I'd recommend testing your hardware first then correct any problems and then try again.

Glad to see all the responses to my post! Thanks everyone.

I had checked the machine out quite a bit before installing 10.04 but I did replace the video card later as the old one didnt stand up.

I actually went out today and installed 9.04 on the machine with no problems and everything worked. Go figure?? 

To answer some questions - I always install from cd. I do at times do a live test just to make sure the video card is not going to be a problem. 

The op about the sharing of the external drive is due to the drive origionally setup as ntfs type partition and probably caused some problems with sharing. I will re partition the drive later after the customer moves their stuff off of it. Probably give it a standart ext3 partition. 

So, I guess the only weird problem is the creating a second user account. Boy was it messed up. But on 9.04 it went without a hitch.

Thanks again everyone for replying!

:D

---

### Post by mörgæs on 2010-09-15
Good that 9.04 worked, but it is running out of support in a month:
[http://en.wikipedia.org/wiki/Ubuntu_lucid_lynx#Version_timeline](http://en.wikipedia.org/wiki/Ubuntu_lucid_lynx#Version_timeline)

---

### Post by coffee412 on 2010-09-15
> **mörgæs said:**
> Good that 9.04 worked, but it is running out of support in a month:
[http://en.wikipedia.org/wiki/Ubuntu_lucid_lynx#Version_timeline](http://en.wikipedia.org/wiki/Ubuntu_lucid_lynx#Version_timeline)

I know :(. But I was backed into a corner and had to do something. My thinking is that any problems will get eventually worked out and then an upgrade can happen.

I run a small repair business and I have clients that are all fed up with viruses and such from MS. So, I install Ubuntu as an alternative. I have to say that they all walk away quite happy. This was the first that I tried 10.04 on and it just didnt go well. But in the end the customer is happy and thats what matters most!

---

### Post by DouglasAWh on 2010-09-15
on the HP nc6400 and on the HP nx9420, secondary monitors still don't work.  Quite a pain.  On an HP 7900, using desktop affects with dual monitors does not work.  I am also unable to get a 3rd monitor working (if someone wants to help me on that, I would be quite happy...pm me :) ).

I'm trying to remember if I had any other problems.

The ability to rotate monitors out of the box on the 7900 was quite nice.  Fedora already had this and I was using Fedora because of it for a while, but Fedora seemed much less stable than the LTS.

---

