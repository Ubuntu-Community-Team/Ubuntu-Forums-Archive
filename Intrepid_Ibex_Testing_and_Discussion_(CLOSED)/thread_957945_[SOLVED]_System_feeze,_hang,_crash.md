---
title: "[SOLVED] System feeze, hang, crash"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dunbrokin on 2008-10-24
I cannot see that anybody else is having the same problem as me....There has been no change to my hardware and Hardy ran perfectly on my machine. However, after updating to Beta I am having about 6 to 10 completer system freezes each day. I have to reboot the whole system to get it back. I cannot replicate the fault and nothing shows in the syslog. It seems to occur when a number of processes are being carried out at the same time, so one would suspect a kernel fault. The last time it happened (about 5 mins ago) I was searching on this forum for a post on the word "freeze"...the information was just about to download when somebody sent me an IM on Pidgin...then complete freeze and restart needed.....it is starting to get wearying....Any suggestions would be appreciated

---

### Post by caryb on 2008-10-24
Try another browser besides FF & see if that fixes it! I had a dodgy FF profile in my home directory giving me the same issues. I had to delete the firefox profile. Just a thought create a new user & log in as them & test that way.


Cary

---

### Post by jerrylamos on 2008-10-24
My IBM Thinkpad R31 freezes on boot.  The problem is compiz playing tricks with the graphics hardware and drivers to produce "eye candy" visual effects.  These tricks can hang things up tighter than a drum.

First thing to try is 
System Preferences Appearance Visual effects 
select none.

That's "supposed to" reduce compiz use.  On an install that will persist to the next boot.

Another way to test is to boot up and in terminal do
sudo meticity --replace &

which is "supposed to" use older simpler metacity desktop graphics code.  This has to be done on every boot.

Since this problem has been chasing me in most Intrepid 8.10 builds since August 12 I commonly do:
install             (doesn't use compiz)
boot in recovery mode
select root prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot.

I've had to do this on Alpha 6, Beta, and now on Release Candidate.
See Launchpad Bug #259385 for more detail.  

Compiz does stay off from boot to boot, and so far even stays off on updates.  If I do sudo apt-get install compiz sudo apt-get install compiz-core the laptop promptly hangs up (freezes) again.

Jerry

---

### Post by dunbrokin on 2008-10-24
> **jerrylamos said:**
> My IBM Thinkpad R31 freezes on boot.  The problem is compiz playing tricks with the graphics hardware and drivers to produce "eye candy" visual effects.  These tricks can hang things up tighter than a drum.

First thing to try is 
System Preferences Appearance Visual effects 
select none.

That's "supposed to" reduce compiz use.  On an install that will persist to the next boot.

Another way to test is to boot up and in terminal do
sudo meticity --replace &

which is "supposed to" use older simpler metacity desktop graphics code.  This has to be done on every boot.

Since this problem has been chasing me in most Intrepid 8.10 builds since August 12 I commonly do:
install             (doesn't use compiz)
boot in recovery mode
select root prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot.

I've had to do this on Alpha 6, Beta, and now on Release Candidate.
See Launchpad Bug #259385 for more detail.  

Compiz does stay off from boot to boot, and so far even stays off on updates.  If I do sudo apt-get install compiz sudo apt-get install compiz-core the laptop promptly hangs up (freezes) again.

Jerry

Yeah, I think this might be the problem rather than the dodgy FF as I have had the freezes even when FF was not in use. Also, I did go for a more jazzed up effects screen in Ibex than I had been using in Hardy. I have set my screen effects now at the lowest level so we will see what happens.

---

### Post by dunbrokin on 2008-10-24
Actually by resetting to the lowest level of screen effects, I now get a black screen blink every so often....this used to happen to me under Hardy also ...but has not happened since I upgraded to Ibex.....I guess there is a link there somewhere.

---

### Post by crashflow on 2008-10-26
After installing todays updates, my system freezes every 15 to 20 minutes on average.

Quite annoying.

---

### Post by dunbrokin on 2008-10-26
> **crashflow said:**
> After installing todays updates, my system freezes every 15 to 20 minutes on average.

Quite annoying.


Have you tried the suggestion above regarding the eye-candy....it worked a treat for me....I have already downloaded today's updates and not had a crash since I changed my eye-candy level.

---

### Post by crashflow on 2008-10-27
> **dunbrokin said:**
> Have you tried the suggestion above regarding the eye-candy....it worked a treat for me....I have already downloaded today's updates and not had a crash since I changed my eye-candy level.

Yes I did and since then the freezes occurred less often. But once in a while they still occur.

And the strange thing is that now the symptoms of the freeze have changed: I can now move the mouse arrow when the system freezes, even if that is the only thing that works. When I still had compiz installed, the mouse arrow froze as well.

---

### Post by dunbrokin on 2008-10-27
> **crashflow said:**
> Yes I did and since then the freezes occurred less often. But once in a while they still occur.

And the strange thing is that now the symptoms of the freeze have changed: I can now move the mouse arrow when the system freezes, even if that is the only thing that works. When I still had compiz installed, the mouse arrow froze as well.


Instead of getting a freeze now, I get a blank screen ocassionally. When I had compiz installed and the system froze, I had the opposite problem...my mouse would work but nothing else would. Sorry I cannot help you any more than this...I am pretty new to Ubuntu myself.

---

