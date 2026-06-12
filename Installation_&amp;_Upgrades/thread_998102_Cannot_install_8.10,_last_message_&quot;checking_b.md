---
title: "Cannot install 8.10, last message &quot;checking battery state...&quot;"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by joke* on 2008-11-30
Hi,
I'm new to ubuntu (well, I've installed 1 time, but that was a failure too, because I was writing a thesis atm and I didn't feel like reïnstalling all my needed programs.  Linux had been on my computer until it was stolen (bastards!), but I never used it...)

So, I'm trying to install Ubuntu (unlike the other time) on an Acer Aspire 5920.  As long as I didn't install, everything went well with the CD, found internet, could actually do things.

Now I was installing it, and I was just partitioning the thing, I think it was just finished, and this code came upon my screen:

> 
Starting System Tools Backends system-tools-backends    [OK]
Starting deferred execution scheduler atd               [OK]
Starting periodic command scheduler crond               [OK]
...
Checking battery state...                               [OK]


It hasn't changed in an hour...

---

### Post by shoo56 on 2008-11-30
Hi, I'm having exactly the same problem with my acer aspire 5920 trying to dual boot with xp. Does anyone have any ideas on how to fix it?

---

### Post by bubbafrye on 2009-01-11
Same here.  I was trying to do a fresh install over an old Dapper Drake I had.  

I loaded up the 8.10 Live CD and chose install from the main menu [not the Live CD environment].

I set location, language, formatted the partition and started installing.  Files were copying and all seemed well until things started loading.  

Right after the "Checking Battery State" line, my screen flickered a few times then sat at the "Checking Battery State" for another hour or so.


The big bummer is that my GRUB loader is busted now [Error 2] and I had to change my BIOS just to get back to my XP drive. [I have Ubuntu on my Primary Master and XP on a separate Primary Slave drive]


Thanks for any feedback!

---

### Post by tark on 2009-01-15
> **bubbafrye said:**
> Same here.  I was trying to do a fresh install over an old Dapper Drake I had.  

I loaded up the 8.10 Live CD and chose install from the main menu [not the Live CD environment].

I set location, language, formatted the partition and started installing.  Files were copying and all seemed well until things started loading.  

Right after the "Checking Battery State" line, my screen flickered a few times then sat at the "Checking Battery State" for another hour or so.


The big bummer is that my GRUB loader is busted now [Error 2] and I had to change my BIOS just to get back to my XP drive. [I have Ubuntu on my Primary Master and XP on a separate Primary Slave drive]


Thanks for any feedback!I have the exact same problem: installation is stuck at "Checking Battery State", then i reset the pc and all i get is that GRUB Error 2.

Do you have any idea how to solve the the problem and get ubuntu and windows xp back?

---

### Post by bubbafrye on 2009-01-15
I was able to get my system up by hitting F4 after booting from the LiveCD.  I then chose to insall in 'safe graphics mode' and got to a stable [800x600] desktop. 

1) Reguarding the nvidia display drivers, here is how I 'fixed' things.  I say 'fixed' because I did this before and it didn't seem to make a difference.

From the Synaptic Pakage Manager, uninstall anything you find related to nvidia [assuming it is display related] - I had about 7 items.

Then follow the steps in the recent thread titled that talks about how much they love the new nvidia drivers. I will upddate with the thread link when I find it again..

2) Access XP again without using GRUB, I had the advantage of reading an old thread a coupld of years back that suggested using seperate physycal drives for your installs - making Ubuntu/GRUB kand on the Master drive and XP on the Slave.  I just changed my BIOS to boot from that drive first for a quick jump to XP before things got sorted out. 

hope that helps - I'll post more details when I get back to my Ubuntu box at home.

---

### Post by bostonvaulter on 2009-01-30
Does anybody have an actual fix for this problem?  I have a similar problem, but I am only getting it when I am trying to update.  I am also using the nvidia drivers.

---

### Post by bubbafrye on 2009-02-02
Here is the thread I was referencing before...
[http://ubuntuforums.org/showthread.php?t=990978&highlight=love+nvidia]("http://ubuntuforums.org/showthread.php?t=990978&highlight=love+nvidia")

again..  my 'rescue' process was to 
- reboot to the LiveCD and enter Safe Graphics Mode [F4].  
- Remove all of the nVidia packages.
- Follow the steps in the posting above to get a clean install of the drivers.


Best of luck.

---

