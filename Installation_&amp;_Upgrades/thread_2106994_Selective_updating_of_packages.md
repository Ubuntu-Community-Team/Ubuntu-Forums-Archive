---
title: "Selective updating of packages"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by sagar13 on 2013-01-20
How can I go about selectively updating packages on ubuntu with my selective policy being, updating only those packages which won't affect the current running processes in the system?

and implicit to the above question, how would I know that which update would affect which running process in the system?

---

### Post by Cheesehead on 2013-01-20
What kinds of processes do you care about getting disrupted? Servers? Web browsers? Media players? Folding clients? Torrents? 

Most userland applications, for example, won't be disrupted. Firefox will beg and plead to be restarted, but won't restart until you okay it.

On the other hand, most daemons will be restarted automatically by root as part of the install.

Various clients and servers fall somewhere in between, depending upon the whims of the developers.

If you will have this issue regularly, perhaps you should adjust your update config to download-only or update-upon-demand instead of scheduled.

---

### Post by tgalati4 on 2013-01-21
There are several update strategies you can use.  Each has good and bad points.  For instance you can delay all upgrades for 6 months.  If everything is working the way you want, you can be reasonably sure it will stay that way.  Then perform several hundred megabytes of updates all at one time and dedicate a day to fixing the things that may get broken.  You must plan for this in advance, because your computer (and printer) will be out of comission for a while.  Although most updates happen with no problems whatsoever, there are edge cases that will bite you.

If you want stability, stick with the LTS releases and only update once a year.  If you read about an important security breach that is only fixed with a kernel update, then perform only that update, leave the rest for the yearly update schedule.

You could update once a quarter, or once a month.  It really depends on your level of pain.  Regardless, you need to be prepared to fix things if an upgrade breaks your graphics, or sound, or printing.  These are called regressions and they come with a complex system like Linux.

To try to only update things that aren't running simply means that when you do try to run them they may be broken and you won't know why.  Instead, you need to update the packages that you use frequently.  Because if they break, you will know right away and you can post bug reports or search for work-arounds in these forums.

There is no ideal system, but you have to weigh stability vs agony.

1.  High Stability and High Agony  Updating once per year.  System runs great during the entire year, but then the yearly mega-update breaks a few things and you need to spend a few days of head-scratching and hair-pulling to get your system back the way it was.

2.  High Stability and Low Agony  Don't update at all, just ignore or remove the update notifier.  Ignorance is bliss and you will never know the pain that you are not experiencing.  Oh, your system will continue to run in a predictable manner.

3.  Low Stability and High Agony.  Update early and often.  Every week update those packages and every week find something new that needs fixing.  Seems like you spend more time tweaking the system than doing real work. In fact Linux in general seems like a continual work-in-progress.  Just when you have your system running the way you want--another update comes out that you just have to install.

4.  Low Stability and Low Agony.  Similar to the state above but with an attitude change.  "I really don't need 3D graphics anymore."  "Sound is overrated."  "I need to remember to plug in my laptop because sleep doesn't work anymore."  System is quite secure because it is up-to-date, but as time goes on, more stuff breaks and you are no longer motivated to fix it.  Sort of like an old car.  "Do I want to pour any more money into it?"

After reviewing these four possible states, I realize that there is no ideal state--*that is the Update Dilemma*.

---

### Post by sagar13 on 2013-01-21
Well, I am trying to design a system that will automate the process of updating only those packages which will not affect the current running processes. If an update is found which shall affect a current running package, then it might just download the update and not install or notify the admin that a particular update wasn't performed since the process is running.

P.S: The processes can be anything.. server, system, user etc.. I mean any freaking running process in the system.

Any pointers..?

---

### Post by dino99 on 2013-01-21
Lets draw the big picture:

ubuntu mainly have 3 releases: LTS, Current & Dev
Each of them have separate repos for: main universe multiverse & proposed

So the most scary are: Dev & proposed (universe & multiverse are used a little only).

When you talk about running processes: they have been started by the system itself and by the programs (apps) loaded by the user(s) (each ones having dependencies).

Thats it, meaning that you might consider the distro release (LTS or Current for stability) and avoid "proposed" archive for the same reason (due to paranoia).

If your system(s)/network have low activity or is stopped (WE, ...) then it can be the best schedule.

---

### Post by sagar13 on 2013-01-21
See, if I shedule DAILY automatic upadation(downloading and installing available updates) of system using cron or somthing, and let's say I have a java program running for 3 days and a java update appears on the 2nd day. So as per my schedule, the system will abort the demon running my java program and update java.

I want a way out of it. Somehow if I can know at the time of updation that java update that's available, will affect my running java program, I'd want that java update does not take place. 3 days later when the java program gets over, then it be should updated.

---

