---
title: "Printing in Jaunty problems"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DariusZelvys on 2009-04-08
Printing in Jaunty is seriously damaged...
It happens with canon 2022 and hp 1320n printers, with all the other printers in office i have not tried yet, but i suspect the same will happen. 
Printers install correctly and then by default they have a US letter format set, which leads to fail printing cause those jobs , cause printers only accept A4 format.
If i set the format to A4 manually it shows that it has changed but it has not. It shows that the job is finished, the document is printed, but it just sends information to printer in US letter format and printer doesn't print. How to fix this issue? Is there some kind of workaround?

---

### Post by DariusZelvys on 2009-04-08
> **DariusZelvys said:**
> Printing in Jaunty is seriously damaged...
It happens with canon 2022 and hp 1320n printers, with all the other printers in office i have not tried yet, but i suspect the same will happen. 
Printers install correctly and then by default they have a US letter format set, which leads to fail printing cause those jobs , cause printers only accept A4 format.
If i set the format to A4 manually it shows that it has changed but it has not. It shows that the job is finished, the document is printed, but it just sends information to printer in US letter format and printer doesn't print. How to fix this issue? Is there some kind of workaround?

bump...no ideas?

---

### Post by skedone on 2009-04-08
have fully updated mate as i had no end of printing problems and it was due to cups still in testing but yesterdays updates fixed all my printing problem

---

### Post by DariusZelvys on 2009-04-08
> **skedone said:**
> have fully updated mate as i had no end of printing problems and it was due to cups still in testing but yesterdays updates fixed all my printing problem

all updates installed still the problem exists

---

### Post by DougieFresh4U on 2009-04-08
Have you tried reinstalling 'foomatic' packages, as I know that was an issue I had a couple of weeks ago when update 'borked' my printer.

---

### Post by DariusZelvys on 2009-04-08
> **DougieFresh4U said:**
> Have you tried reinstalling 'foomatic' packages, as I know that was an issue I had a couple of weeks ago when update 'borked' my printer.

I'm newcomer, how should i do it?

---

### Post by DougieFresh4U on 2009-04-08
> **DariusZelvys said:**
> I'm newcomer, how should i do it?

Go into **System>Administration>Synaptic Package Manager**
scroll down to 'foomatic' and right click each one that is already installed and click 'Mark For Reinstallation'
Screenshot shows the ones I have installed

---

### Post by DariusZelvys on 2009-04-08
> **DougieFresh4U said:**
> Go into **System>Administration>Synaptic Package Manager**
scroll down to 'foomatic' and right click each one that is already installed and click 'Mark For Reinstallation'
Screenshot shows the ones I have installed

Didn't help, but thanx for a try. Any other suggestions?

---

### Post by DariusZelvys on 2009-04-08
> **DougieFresh4U said:**
> Go into **System>Administration>Synaptic Package Manager**
scroll down to 'foomatic' and right click each one that is already installed and click 'Mark For Reinstallation'
Screenshot shows the ones I have installed

Update on problem. 
reinstalling foomatic helped to print on hp printer, still the same problem exists on Canon 2022i printer... What might be the cause?

---

### Post by DougieFresh4U on 2009-04-08
> **DariusZelvys said:**
> Update on problem. 
reinstalling foomatic helped to print on hp printer, still the same problem exists on Canon 2022i printer... What might be the cause?

Well, at least you got half-way there. My printer was 'hp' so I am not sure on the Canon. Maybe try looking for 'cups' and reinstalling those packages.
Glad I could help some):P

---

### Post by nystire on 2009-04-09
Have you opened a bug report on Launchpad?

---

### Post by DariusZelvys on 2009-04-10
> **nystire said:**
> Have you opened a bug report on Launchpad?

no i didn't

---

### Post by DariusZelvys on 2009-04-10
> **nystire said:**
> Have you opened a bug report on Launchpad?

Reinstalling CUPS packets didnt help

---

### Post by nielz on 2009-04-15
I've got a similar problem: once I change from letter -> a4 the first few lines lines are offset to above the page. None of the suggestions in this thread worked and it's occuring both on a Color LaserJet 3600 and a LaserJet 1320 (Both are attached to a lan) regardless of the driver I use.

---

### Post by DariusZelvys on 2009-04-22
Tommorow is the release day ... and as far as i understand i will not be able to use ubuntu... sad..

---

### Post by rubinstein on 2009-04-22
You will be able to use Ubuntu:

Look at bug #357732 [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/357732](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/357732)
and follow these steps as described in the bug report:

FIX:
# (For simplicity, just paste this section to a terminal.)
# Download the attached pstopdf and install it in /usr/lib/cups/filter/
cd /tmp
wget [http://launchpadlibrarian.net/25537150/pstopdf](http://launchpadlibrarian.net/25537150/pstopdf)
sudo cp pstopdf /usr/lib/cups/filter/
# Then change the permissions of the installed file:
sudo chmod ugo+rx /usr/lib/cups/filter/pstopdf
# that's all.

---

### Post by DariusZelvys on 2009-04-22
The last suggestion didn't help, but i think i found a workaround...
login as root

go to /etc/papersize

in my file i saw only "letter" written in, and no matter what kind of source i set in drivers and printer configuration it used to send it in letter format, and just stuck or cut the first 2 centimeters from top. I just deleted the record "letter" and wrote "a4" :) and it worked. It prints like a charm, but if i want to print in a3 mode, i have to change this file once again, which is not really comfortable. Any suggestions? It seems that drivers cannot write to this file... am i missing something?

---

### Post by dgavenda on 2009-04-22
Having serious printing problems in Jaunty RC.  I just 'upgraded' from 8.10 to Jaunty on Monday.  So, Sunday...printing worked as expected.  This computer is my print server.  Monday, not so much.  Can't print anything.  The printer is a Canon MP530.  A laptop w/ 8.10 on it still can print w/o problems.  It's definitely something in Jaunty.  

Here is the error_log:

/var/log/cups$ tail -f error_log
E [21/Apr/2009:17:04:32 -0500] cupsdAuthorize: Local authentication certificate not found!
E [21/Apr/2009:17:04:39 -0500] Resume-Printer: Unauthorized
E [21/Apr/2009:17:04:39 -0500] cupsdAuthorize: Local authentication certificate not found!
E [21/Apr/2009:17:04:43 -0500] Cancel-Job: Unauthorized
E [21/Apr/2009:17:05:10 -0500] PID 1406 (/usr/lib/cups/filter/rastertogutenprint.5.2) crashed on signal 11!
E [21/Apr/2009:17:05:10 -0500] cupsdAuthorize: Local authentication certificate not found!
E [21/Apr/2009:17:05:10 -0500] cupsdAuthorize: Local authentication certificate not found!
E [21/Apr/2009:17:05:10 -0500] cupsdAuthorize: Local authentication certificate not found!
E [21/Apr/2009:17:05:12 -0500] [Job 78] Job stopped due to filter errors.
E [21/Apr/2009:17:05:12 -0500] cupsdAuthorize: Local authentication certificate not found!


Anyone have something similar?  Created a bug at: [https://bugs.launchpad.net/ubuntu/+bug/364877](https://bugs.launchpad.net/ubuntu/+bug/364877)

---

