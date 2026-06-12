---
title: "Setting time zone"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by TTL on 2006-08-24
Hello,
I have the problem that the time of the applications do not fit with the time of the KDE control panel. I have set the BIOS to my local time and now I get the right time If I create a file, send mails and so on. But the KDE control panel KDE is displaying +2 hours. The control panel displays **Current local timezone Europe/Berlin (UTC)**.
Entering **date** I get my local time reportet as UTC time. For me it looks like some parts of my operating system believes the BIOS is set to UTC and some other parts believe the BIOS is set to my local time.
How do I tell everything of my system the BIOS is set to local time?

---

### Post by halfvolle melk on 2006-08-24
Hi TTL,
You can probably fix this by setting UTC=yes to UTC=no in etc/default/rcS.

---

### Post by TTL on 2006-08-24
Thank you I did not know where to find this settings. It was set to **no**, I have changed it to **yes** changed the clock in the BIOS to UCT time and restarted but it did not changed anything. Creating a file (touch) or send a messages with Kopete still displays times two hours in the past.

---

### Post by TeatroAbsurdoAshes on 2007-07-18
> **TTL said:**
> Thank you I did not know where to find this settings. It was set to **no**, I have changed it to **yes** changed the clock in the BIOS to UCT time and restarted but it did not changed anything. Creating a file (touch) or send a messages with Kopete still displays times two hours in the past.
I having a same problem without any way to fix it...Why this happen? How and who do design this ridiculous and unnecessary struggle around the time? I love Ubuntu but impossible to got any real answer about this issue...Linux pointing to Windows but in this case this is just a joke..Universal time or local time mean nothing if the time is NOT RIGHT!!!
I spent more time to find out answer for this problem what I am usually spent to work on my computer. What a childish thinking. Ubuntu not ready to replace the corrupted Windows..just on other way to create struggle around computing. So many excellent brain around here and few(?) basic just fly a way!
Sorry for this!

---

### Post by wpshooter on 2007-07-18
> **TeatroAbsurdoAshes said:**
> I having a same problem without any way to fix it...Why this happen? How and who do design this ridiculous and unnecessary struggle around the time? I love Ubuntu but impossible to got any real answer about this issue...Linux pointing to Windows but in this case this is just a joke..Universal time or local time mean nothing if the time is NOT RIGHT!!!
I spent more time to find out answer for this problem what I am usually spent to work on my computer. What a childish thinking. Ubuntu not ready to replace the corrupted Windows..just on other way to create struggle around computing. So many excellent brain around here and few(?) basic just fly a way!
Sorry for this!

Teatro...:

I agree.  This having the BIOS showing one time and the O/S showing another time has always seemed just a bit weird to me !!!

---

### Post by Phil Baxter Jr. on 2007-07-18
> **TeatroAbsurdoAshes said:**
> I having a same problem without any way to fix it...Why this happen? How and who do design this ridiculous and unnecessary struggle around the time? I love Ubuntu but impossible to got any real answer about this issue...Linux pointing to Windows but in this case this is just a joke..Universal time or local time mean nothing if the time is NOT RIGHT!!!
I spent more time to find out answer for this problem what I am usually spent to work on my computer. What a childish thinking. Ubuntu not ready to replace the corrupted Windows..just on other way to create struggle around computing. So many excellent brain around here and few(?) basic just fly a way!
Sorry for this!

Ok, IBM T-22, Have had a number Bios time changes.  This AM IBm instead of booting Ubunto, started up Bios which showed time increased 7 hours (Sonoma CA).  Corrected Bios time.  Then found Ubuntu time also wrong,  Last night Ubuntu closed AOK, no problems.  No other program or system run.

Just what is going on here?  About a week ago out of town same thing happened plus the order of HDD on startup changed with net put ahead of HDD's.  Needless to say, impossible to start ubuntu.  It is said Ubunto mostly free of outside influence.  Does not seem so here.  

So sad, seemed like a good program and a welcome shift away from MS.

---

### Post by dabl on 2007-07-18
It happens that I have an installation of another Debian Linux distro, e-live, on another hard drive on the same platform where I run Ubuntu and Kubuntu.  Guess what -- e-live thinks I'm on "Alaska Daylight Time" (4 hours behind my Eastern Daylight Time).  I attempted to fix it by changing the UTC= option in /etc/default/rcS, but it didn't fix it.  I can change it with the "date" command, but of course that only lasts for the running session.

Anyway, it appears to be a larger problem that just Ubuntu ... by the way, my Ubuntu system shows the time correctly.  :rolleyes:

---

### Post by Phil Baxter Jr. on 2007-07-19
> **Phil Baxter Jr. said:**
> Ok, IBM T-22, Have had a number Bios time changes.  This AM IBm instead of booting Ubunto, started up Bios which showed time increased 7 hours (Sonoma CA).  Corrected Bios time.  Then found Ubuntu time also wrong,  Last night Ubuntu closed AOK, no problems.  No other program or system run.

Just what is going on here?  About a week ago out of town same thing happened plus the order of HDD on startup changed with net put ahead of HDD's.  Needless to say, impossible to start ubuntu.  It is said Ubunto mostly free of outside influence.  Does not seem so here.  

So sad, seemed like a good program and a welcome shift away from MS.

More on "Time" 19 Jul 07.  Got curious to dig through the question.  Find both Windows XP & 7.04 Ubunto seem stuck on relationship to UTC aka GMT time systems.  Find this as bold non-functional on system of both parties.  "Kid Like" attitude of do it my way.  Now beyond sad to approaching outrage.  Then poked into 7.04 "Adjust Date & Time".  Found development of 7.04 does not do as it says.  Offers to install "NTP".  Not!  One has to adjust time manually, can possibly use one syncronous time click.  Win XP also questionable as will auto adjust time to local internet if time is off.

In either system the displayed bios time is changed.  Doing such leaves opening also for outside access to one's computer.  Good time for a great choice.  Make a functional decision to permit the computer built in clock do what it was made to do.  Why not display both UTC/GMT and local time and leave it?  Wobbly weak and unnecessarily open as is.  Phil B

---

