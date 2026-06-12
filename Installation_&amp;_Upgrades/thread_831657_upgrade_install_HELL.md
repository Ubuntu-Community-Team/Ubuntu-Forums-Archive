---
title: "upgrade install HELL"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by circusmonkey on 2008-06-17
what a nightmare it is to get the new Ubuntu working ...

1 ) According to this tutorial I should see my xp 32 bit install and then move the slider to define the space for my Ubuntu install. Needless to say no xp install is defined. The first time I tried this I wiped my xp install. 
Also the Ubuntu partition manager does not even pick up the names of my NTFS drives, so I don't have a clue what drive is what and where is safe to install ?!?!?!? 

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

2) During  the first disaster install , I tried to connect to the internet.unlike v 7.10 the new version refuses to connect.So naturally you go to the help. What a waste of time , the help states I should automatically be connected to the Internet as I connect through a router and an always on internet connection...
and of course it doesn't work !!!!!. So what next , follow some steps that give no clue what so ever for getting the internet connection working. Finally the help refers me to look online for help .. What a joke

3) Running the upgrade from my WORKING version 7.10 just wrecked it  why would this be ever advised by anyone is baffling 

It seems to me this version is worse than the last for installation.As ever a great way to attract new users ...... 

Not impressed

---

### Post by overdrank on 2008-06-17
> **circusmonkey said:**
> what a nightmare it is to get the new Ubuntu working ...

1 ) According to this tutorial I should see my xp 32 bit install and then move the slider to define the space for my Ubuntu install. Needless to say no xp install is defined. The first time I tried this I wiped my xp install. 
Also the Ubuntu partition manager does not even pick up the names of my NTFS drives, so I don't have a clue what drive is what and where is safe to install ?!?!?!? 

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

2) During  the first disaster install , I tried to connect to the internet.unlike v 7.10 the new version refuses to connect.So naturally you go to the help. What a waste of time , the help states I should automatically be connected to the Internet as I connect through a router and an always on internet connection...
and of course it doesn't work !!!!!. So what next , follow some steps that give no clue what so ever for getting the internet connection working. Finally the help refers me to look online for help .. What a joke

3) Running the upgrade from my WORKING version 7.10 just wrecked it  why would this be ever advised by anyone is baffling 

It seems to me this version is worse than the last for installation.As ever a great way to attract new users ...... 

Not impressed

HI and I am sorry to hear of you issues but are you asking for assistants or just venting? I have heard that some users have had issues with multiple drives and is this the case for you? Have you checked the cd for errors as this has been a case for me in the past.

---

### Post by circusmonkey on 2008-06-17
I am just so pissed off we are upto v8.04 and its still a pain in the *** to install and run with the upgrade not working , the help stating facts that are not true. The pages and pages of upgrade  / install hell say it all. 

> I have heard that some users have had issues with multiple drives and is this the case for you? Have you checked the cd for errors as this has been a case for me in the past.

So your saying multiple drives could be an issue ? or the cd .. It really doesn't get better does it.

---

### Post by Pumalite on 2008-06-17
Did you do md5sum? Did you burn at 4x or less? Did you check CD integrity before attempting to upgrade from it?

---

### Post by circusmonkey on 2008-06-17
The cd was fine , as after wrecking my 7.10 and then destroying my XP I did a clean fresh install onto a separate drive from anything else. but as of yet I cannot still connect to the net.

---

### Post by Pumalite on 2008-06-17
To do an upgrade; you have to remove all third parties from your /etc/apt/sources.list and have your OS totally updated before attempting an upgrade.

---

### Post by ChameleonDave on 2008-06-17
> **circusmonkey said:**
> the Ubuntu partition manager does not even pick up the names of my NTFS drives, so I don't have a clue what drive is what and where is safe to install
I can help you find out which drive is which, if you like.

> **circusmonkey said:**
> 
no clue what so ever for getting the internet connection working. Finally the help refers me to look online for help .. What a joke

Not really.  You obviously are able to access the internet.

You had the networking functioning correctly on Gutsy.  Do you know if there was any configuration you had to do for that?  Have you done a search on these fora for posts asking about connection problems?

> **circusmonkey said:**
> 
3) Running the upgrade from my WORKING version 7.10 just wrecked it  why would this be ever advised by anyone is baffling 

I don't think it is advised at all.  I myself did such an upgrade out of laziness, despite all the advice on the site that said to do a fresh installation.  It worked, but there were a few bugs, so I eventually decided to do a fresh installation anyway.  

> **circusmonkey said:**
> 
Not impressed
You should be impressed that a totally free operating system works at all, and so well too.  I've used Windows since the 90s, and I can't begin to tell you all the problems I've had installing the OS, connecting various machines to the internet, dealing with viruses, etc.

---

### Post by Bubba64 on 2008-06-17
> **Pumalite said:**
> To do an upgrade; you have to remove all third parties from your /etc/apt/sources.list and have your OS totally updated before attempting an upgrade.

Yes this is so correct, especially if you in the past have used automatix to do package installs.

---

### Post by circusmonkey on 2008-06-17
Hey ChameleonDave

> I can help you find out which drive is which, if you like.

sure anything has to be better than unplugging all my SATA drives


> Not really. You obviously are able to access the internet.

You had the networking functioning correctly on Gutsy. Do you know if there was any configuration you had to do for that? Have you done a search on these fora for posts asking about connection problems?

Nice try I had to borrow a lappy from work. So if I had not had that I would of had to install xp or 7.10 all over again just to read how to connect to the internet. So the help does need addressing. 7.10 connected to the net from install. 

> I don't think it is advised at all. I myself did such an upgrade out of laziness, despite all the advice on the site that said to do a fresh installation. It worked, but there were a few bugs, so I eventually decided to do a fresh installation anyway.

If its not good to do and quite obviously will break. Why on earth after you have updated 7.10 OS does it give you the option to upgrade from within the manager !!?!?!?. 

> You should be impressed that a totally free operating system works at all, and so well too. I've used Windows since the 90s, and I can't begin to tell you all the problems I've had installing the OS, connecting various machines to the internet, dealing with viruses, etc.

If the upgrade to 8.04 was so good there would not be so many people starting threads complaining how bad it is and how much trouble they are having.

---

### Post by Pumalite on 2008-06-17
Most of them do not know how to prepare for an upgrade. I've done many without problems.

---

