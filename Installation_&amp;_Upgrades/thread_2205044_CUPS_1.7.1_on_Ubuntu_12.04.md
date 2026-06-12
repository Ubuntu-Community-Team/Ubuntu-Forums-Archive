---
title: "CUPS 1.7.1 on Ubuntu 12.04"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by Casey_Friday on 2014-02-11
I recently lost the ability to AirPrint on my Ubuntu 12.04 box.  I checked, and it was running CUPS 1.5.3, so naturally I wanted to upgrade it to the latest version of cups.  I apt-get --purge remove'd it, and I tried to build the CUPS package from source on their site.  When I try to start the deaemon with service cups start or /etc/init.d/cupsd start, I get:

```
cupsd: Child exited with status 127
cups: unable to start scheduler.
```

Is CUPS 1.7.1 incompatible with Ubuntu 12.04?  Just curious, as I'll likely need to reinstall the old version if this is the case...

---

### Post by tgalati4 on 2014-02-12
When 12.04 was built CUPS was at version 1.5.3.  Trying to build a newer version means there is a possibility that some of the frameworks that CUPS 1.7.1 requires will not be available on 12.04.  This is called *dependency file hell*.  

So AirPrint was working and then it stopped working?  Was there a particular update that you performed recently?  Have you look at the CUPS log files for clues.  (/var/log/cups)  Let's go back to the original CUPS (1.5.3) and try to figure out why there was a regression.  I would only attempt to install 1.7.1 if there was some new feature that you absolutely had to have.  Printing is pretty basic.  It either works or it doesn't.  So let's focus on getting it working.

Sometimes just deleting the printer and recreating it can fix the problem.  Sometimes a reboot is needed then check for any software updates.  There were some CUPS bugs fixed with updates.  Make sure you are running the latest 12.04 version.

---

### Post by Casey_Friday on 2014-02-12
I figured it was something like file dependency.  I just tried to remove all instances of 1.7.1, and I'm currently reinstalling 1.5.3 to see if I can get AirPrint working again.  I guess the thing is, I didn't do anything special to set up AirPrint, it 'just worked' from my iPad when I initially set up my HP printer (CUPS drivers as well as HP's drivers).  When it stopped working, I just figured reinstall the newest version of software since a reboot / service restart didn't fix anything.

I'll report back when I've got 1.5.3 up and running again.

---

### Post by Casey_Friday on 2014-02-12
Brilliant!  It seems uninstalling / reinstalling everything was just the key.  I had a bit of trouble getting all the files out of the system (cups.conf, etc) from the build from source I did, but I finally got them all out, and I did an apt-get -f install cups and got the 1.5.3 server running again.

Reinstalled the printer, updated sharing, and now it's showing on my iPad again.  If it disappears again, I'll check the logs to see what changed.

Thanks for your help!  (I wouldn't have even known to stick with 1.5.3 without your post)

---

### Post by tgalati4 on 2014-02-12
Spend some time reviewing the changes between 1.5.3 and 1.7.1 and summarize for us.  What is the killer feature that you just have to have?  Since Apple bought CUPS there is probably a lot of activity to support Apple devices, but if your current system works, there is no need to change.  Newer is not always better.  You need to consider the release notes whenever a new package comes out.  The typical mac reponse--"Oooh shiny, I must have it"--doesn't really apply to linux.  If it works, don't mess with it.  

I'm glad you got it sorted out.

---

### Post by Casey_Friday on 2014-02-20
To be honest, it was completely the "It's new and shiny, it MUST be better!" mentality that got me.  My HP Photosmart C4150 was purchased over seven years ago, and it's still going strong.  I have it plugged into my Ubuntu box, and I wanted to be able to print to it from all my machines.  There's not much more I could do with it, save for scanning remotely (but I believe that's SANE utils).

Agreed re: if it works, leave it alone.  It's just that it stopped working, so I figured, why not upgrade?  Nonetheless, it sorted itself.

---

### Post by tgalati4 on 2014-02-20
If you really want shiny, wrap your printer:

[ATTACH=CONFIG]250541[/ATTACH]

Trying getting a 5-year-old Apple product to integrate with anything.

---

### Post by Casey_Friday on 2014-02-24
LoL - lots of color choices!

Not sure what your point about Apple is, I currently use a 2011 MBP, and it integrates with just about everything.  Perhaps you're talking about the Apple product 'CUPS'.

---

### Post by tgalati4 on 2014-02-24
No, I am talking about my Apple Powerbook (PPC architecture) that was promptly dropped after 5 years, even though it still runs well.  Ask others who were left behind when Apple changed architectures in the past.

---

### Post by Casey_Friday on 2014-02-24
Yeah, that is pretty painful.

---

### Post by sgualembro on 2014-03-04
I've done the same error but now I dont know how can remove all instances of cups 1.7.1. and if I try to reinstall cups 1.5.3 I have a lot of errors of dependency... :(

---

