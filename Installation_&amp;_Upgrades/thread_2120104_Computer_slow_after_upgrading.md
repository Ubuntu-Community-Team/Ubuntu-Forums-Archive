---
title: "Computer slow after upgrading"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by bthomson100 on 2013-02-25
I've just upgraded from Ubuntu 10 to 11 and then 12.04.1 and my computer has now become a turtle. Every minute or so, the screen dims (white spaces become grey) and the computer seems to be off doing something which takes anywhere from 10 seconds to several minutes. The disk drive light shows no disk activity during these freezes. It seems to happen most in Thunderbird (v. 17.0.2) but happens in other applications as well. I have uninstalled and reinstalled Thunderbird but that hasn't changed anything.

I'm using an Asus EEE 1005HA netbook with 1.5GB of RAM and a 160 GB HD with 6GB free.

My computer has become almost useless as a result since I'm not able to do any work while waiting for the computer to react to even simple commands like resorting mail, typing in an email address, switching folders, etc.

Can anyone PLEASE help with suggestions as to what this so call upgrade has done to make my computer useless! I'm getting close to desperate.

Bob Thomson
Ottawa, Canada

---

### Post by windscape on 2013-02-25
Hi,

The Unity interface in 12.04.1 requires hardware OpenGL acceleration which your system apparently does not support very well. I recommend installing another desktop environment such as Xubuntu or Lubuntu which are a lot less resource demanding.

---

### Post by bthomson100 on 2013-02-25
Does this mean that Ubuntu 12.04 requires that many more computer resources than version 10? Are you reasonably sure this might be a resource problem?

Sorry for the questions. I should have indicated that I'm pretty new to this, although not a complete newbie.

Bob

---

### Post by ajgreeny on 2013-02-25
Yes, most netbooks find unity desktop too resource hungry.

I suggest you try Xubuntu 12.04 which has another 2 yrs support, or if you really prefer gnome see [12.04 LTS Gnome Classic]("http://ubuntuforums.org/showthread.php?t=1966370")for a way to get the old classic gnome desktop which may run better than unity on that hardware.

PS:
With only 6GB free of your 160GB disk, you may see slow downs from there being insufficient space available.

---

### Post by presence1960 on 2013-02-25
You can also install from Ubuntu Software Center xfce or lxde desktop environments. Once installed reboot and when you get to the log in window you can choose which desktop session to log into by clicking the little circular symbol top right of password dialogue box. xfce and lxde will relieve the pressure from your RAM and CPU, however your hard disk is almost full. The only thing that will fix that is to get rid of some things on your disk. If your disk remains over 90% full nothing will help speed things up.

---

### Post by bthomson100 on 2013-02-26
Thanks for all your suggestions. I would NEVER have figured out that you have to click the little circle above the password box to choose between desktop types. Why don't they document these things.

I installed Xubuntu 12.04, freed up about 10GB on my hard drive (I now have 15GB free), deleted all the MSF index files in Thunderbird and am running Xubuntu in Xfce now. I saw a reference to something called Ubuntu Utility Integration addon in Thunderbird which can slow it down, but I haven't been able to find anything about addons in Thunderbird to disable it.

It SEEMS to be better, but I'm still experiencing "long" delays in switching between applications.

Now I can't access LibreOffice which this "upgrade" has forced me to accept over the old Open Office. I'm too much of a newbie to know how to find the programme and put an icon for it on the desktop. There seems to be no end to problems. Now the writing cursor in this editor keeps jumping to the place where the arrow cursor is, forcing me to go back and erase text I've typed into the middle of the text where the arrow was.

I'm almost ready to go back to Microsoft after 2 years with Ubuntu, despite it being against all my principles, because I need the computer to do important work and it is now barely functional.

I've wasted pretty much a whole day now on this "upgrade".

Bob

---

### Post by bthomson100 on 2013-02-27
I FINALLY found the problem and think I've solved it. The Ubuntu upgrade installed a Thunderbird extension called EDS Contact integration which added a personal address book to Thunderbird with 5000+ blank entries and another address book called either Google or "Unbuntu One", depending on which computer I was using. When deleting the "personal" address book, I got an error message saying "Sorry, this version of EDS Contacts does not support deleting Evolution address books". When I deleted the personal address book, the Google and/or Ubuntu One address book disappeared too.  It reappeared however when I rebooted Thunderbird.

Then I finally found the "add-ons" menu in Thunderbird and then the EDS Contacts extension which I disabled.  This appears to have given me back email connectivity.

Google searches, Ubuntu and Thunderbird forum searches failed to turn up any references to this problem! I can't believe others haven't experienced it.

Is there anywhere I can leave a note for anyone (probably a newbie) who searches for a solution to this problem so they don't have to waste two days of their time and probably several days off their lifespan because of the frustration and tension this generates?

Bob Thomson
Ottawa, Canada

---

### Post by mörgæs on 2013-02-28
> **bthomson100 said:**
> 
Is there anywhere I can leave a note for anyone (probably a newbie) who searches for a solution to this problem so they don't have to waste two days of their time and probably several days off their lifespan because of the frustration and tension this generates?


Best is to mark the thread 'solved' - which is not available right now as the forum software is being upgraded.

Besides, there seems to have been made so many changes on this poor computer that I would suggest a clean install.

---

