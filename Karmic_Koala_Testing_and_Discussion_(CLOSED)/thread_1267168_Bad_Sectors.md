---
title: "Bad Sectors"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by anotherdisciple on 2009-09-15
I am running 9.10 Alpha 5 (64-bit) and it pops up a warning about disk failure. It says that my disk passed, but in small text it says that it has bad sectors. I believe that I ran a chkdsk from windows not long ago and all was well. Is there any way to confirm bad sectors?

---

### Post by ElSlunko on 2009-09-15
Lots of threads about this. It's a bug and you can disable it. Sorry for not having proper links but a quick search will get you to your answer.

---

### Post by cariboo on 2009-09-15
This has come up several time s before, The applet will tell you how many bad sectors there are, and on at least my system it will tell you the threshold, eg: when to start worrying.

I downloaded and ran the diagnostic tools from my hard drive manufacturer, which gave the hard drive in question a clean bill of health.

Be aware that that your hard drive is failing, but it may last quite a while before complete failure.

If you want to try another tool, gsmartcontrol is in the repositories.

---

### Post by psyke83 on 2009-09-15
> **cariboo907 said:**
> This has come up several time s before, The applet will tell you how many bad sectors there are, and on at least my system it will tell you the threshold, eg: when to start worrying.

I downloaded and ran the diagnostic tools from my hard drive manufacturer, which gave the hard drive in question a clean bill of health.

Be aware that that your hard drive is failing, but it may last quite a while before complete failure.

If you want to try another tool, gsmartcontrol is in the repositories.

Honestly, I don't think so. If a hard drive has one reallocated sector, for example, it doesn't necessarily imply that the drive is starting to fail. I do vaguely recall reading somewhere that some brand new drives would ship from the manufacturer with a bad sector or so (which gets reallocated), but it's still considered healthy.

Remember that SMART values need to also be interpreted over time (e.g. if the high-importance attributes are increasing over a period of a few weeks or so, then it would suggest a failing drive). Then again, drives can also fail before SMART warns of problems.

---

### Post by Seventh Reign on 2009-09-15
Considering it says that 5 brand new right out of the box never before used HDD's (2 Seagates, a WD, and 2 Hitachi's) are failing, I'm fairly convinced there's a major bug with the program.

---

### Post by awlhawk on 2009-09-15
> **Seventh Reign said:**
> Considering it says that 5 brand new right out of the box never before used HDD's (2 Seagates, a WD, and 2 Hitachi's) are failing, I'm fairly convinced there's a major bug with the program.

What's more interesting - that the devs from Ubuntu and Fedora seem to imply that it won't get fixed any time soon, so if you don't like it deal with it (or remove it or fix yourself) which begs the question - why include such a buggy stuff into the distro and run it at startup every time?

---

### Post by cariboo on 2009-09-15
It's not a bug, it's reporting that there are bad sectors, that's all.

Hard drives start to die the day you first power them up. It's just a matter of how long it takes for them to become unusable. :)

---

### Post by psyke83 on 2009-09-16
> **cariboo907 said:**
> It's not a bug, it's reporting that there are bad sectors, that's all.

Hard drives start to die the day you first power them up. It's just a matter of how long it takes for them to become unusable. :)

Yes. We should also write a little notification app for users: "Warning! Human life expectancy is approximately 65 years. Your life could fail at and moment and may need to be replaced."

If the developer of the application doesn't recognize that the bad sector warning is overkill, I suspect that it's simple pig-headedness. I suspect that someone will need to write to some hard drive manufacturers and/or to the standards body that ratified SMART, and get them to explain to the developers that reallocated bad sectors are *not* a sign of drive failure unless is has exceeded the threshold defined by the manufacturer (which is encoded in the drive's SMART attributes), or the reallocated sectors are increasing over time.

I have a 5 year old drive which as exactly one reallocated sector since the first day of use, and five years later it has developed no other reallocated  or bad sectors (such as offline uncorrectable) or SMART failures.

Edit: Let me just clarify something. I'm opposed to the notification of reallocated sectors only because it is a constant nag to users. It will desensitize people so that when SMART (through palimpsest) detects real signs of impending failure, users will most likely ignore any further warnings. Having a "do not show this warning again" option would solve the problem, I think.

---

### Post by froggyswamp on 2009-09-16
Is this how we want to compete with Apple in Karmic? By confusing users into buying a new HDD?
Good idea putting a hysteric message on each startup and then cynically explaining somewhere else that "Failing disk" doesn't imply what the label says. Does Canonical realize how many upset and confused users this is gonna deliver after official launch?

Fedora 11 ships with this "half-baked" app, it's one of few important reasons (weird behavior and bugs) why people migrated to Ubuntu, I don't want Canonical to copy Fedora's bad decisions (not trolling on Fedora, I really mean it).

---

### Post by VMC on 2009-09-16
I agree that I don't think it was *smart* of the developers to include a program that will just excite users for no reason.

They need to dumb down that SMART program :)

---

