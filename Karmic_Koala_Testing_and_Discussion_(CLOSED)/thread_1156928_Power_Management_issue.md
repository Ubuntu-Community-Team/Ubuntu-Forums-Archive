---
title: "Power Management issue"
date: 2009-05-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-05-12
After yesterdays updates, (there were Power Management updates) my screen will go 'blank' after about 30 seconds of leaving it 'alone'. When I move mouse or touch keys it comes back. I have screensaver unchecked and all power management set to 'never' and I could leave my box alone over nite and it would never go blank.
This only started yesterday.
Has any one else seen this?

---

### Post by Toe on 2009-05-12
Same bug here - must have been introduced by the recent updates of hal.

---

### Post by DougieFresh4U on 2009-05-12
> **Toe said:**
> Same bug here - must have been introduced by the recent updates of hal.
Thanks, thought maybe it was just me as there have been over 60 'visits' and no one has mentioned any thing.
Now, how would one look for 'error'?

---

### Post by autocrosser on 2009-05-13
I've been having similar issues--I would wait until after the alpha release--I'm betting Hal is going to be bounced around a bit this time.................

I must admit, I've wanted my monitor to sleep for about 2 years now & it never seemed to happen until the last update....goes from 62W down to 2W sleeping & as my system stays on 24/7--that can be more than a bit of power savings....

---

### Post by davideotape on 2009-05-13
There's a bug report here: [https://bugs.launchpad.net/ubuntu/+bug/375564](https://bugs.launchpad.net/ubuntu/+bug/375564)

---

### Post by ronacc on 2009-05-13
I'm on 64bit here with an amd64x2 and default settings for screen saver and pwr management , and I am not seeing this here .

update: after I posted the above I decided to check just what the defaults were , so I opened up prefs>screensaver and just looked , I did not change anything I also looked at powermanagement  , my screen was blanking ( blank screen no pattern ) after ~ 5 minute prior to checking , the settings were blank screen after 10 min and pwr management never and display to sleep after 35 min . now after just checking and changing nothing my display still hasn't blanked after 45 min so I appear to have the opisite effect ?

---

### Post by DougieFresh4U on 2009-05-16
There were updates this morning for 'hal' and 'gnome power manager' but they did not fix the sleep issue  :mad::mad:

---

### Post by autocrosser on 2009-05-16
Crud---looks like I opened another thread on this---could a mod merge the threads---

YA--it's getting bad for me--now that I look at the report--I see that I may be having a separate issue.................

---

### Post by Didius Falco on 2009-05-17
I'm being affected by this as well. Interestingly, it doesn't matter what I set the Screeensaver and/or Power Management to, it still kicks in after roughly 60 seconds of inactivity.

---

### Post by ronacc on 2009-05-17
trying to duplicate your problem I set screensaver to random and 5 minutes , left powermanagement as my above post . screensaver kicks in after 5 minutes as set , will not return to desktop with mouse movement but does return with key board input . so something is strange there but affecting us differently .

---

### Post by ranch hand on 2009-05-18
For me, the delay is 57 seconds.  Everything set to run forever.  No screensaver.

---

### Post by tghe-retford on 2009-05-18
This affects me if I set the display to sleep to 'never'. However, if I set it to '2 hours and 1 minute', I don't get any problems (don't need to leave the computer for that long).

---

### Post by DougieFresh4U on 2009-05-18
> **tghe-retford said:**
> This affects me if I set the display to sleep to 'never'. However, if I set it to '2 hours and 1 minute', I don't get any problems (don't need to leave the computer for that long).
I tried that and it seems to work, no more 'sleep' after 30 seconds. But hopefully they will fix it properly.
Thanks

---

### Post by autocrosser on 2009-05-18
I'll try that to see if it fixes my issue---Thanks!!!!

---

### Post by ancleessen4 on 2009-05-30
This problem persists on my 64bit machine.
I can get around it by setting power management sleep option to 2 hours 1 minute.
How long before this is fixed do you reckon?

---

### Post by bgiannes on 2009-06-29
i seem to be having this problem on my HTPC ubuntu 9.04, w/ 40" LCD?

after some lenght of time (maybe over 1hour?) the screen goes blank. Even those it's set to never. 

Since i'm using my IR remote most of the time, (which the PC don't regade as activity?) the screen goes into stand down, which seems to hang the system, if there is video playing. (doesn't like the video card going into stand down?) If i move the mouse a bit every 60min it never happens.  If there is no video playing the screen just comes backup w/ mouse movment.

---

