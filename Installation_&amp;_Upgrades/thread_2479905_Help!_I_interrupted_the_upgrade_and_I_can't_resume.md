---
title: "Help! I interrupted the upgrade and I can't resume it"
date: 2022-10-12
forum: Installation &amp; Upgrades
---

### Post by stargazer4587 on 2022-10-12
Hello, I am not a beginner, but not a pro, not at all.

I was following this [https://blog.eldernode.com/upgrade-ubuntu-18-04-to-22-04/](https://blog.eldernode.com/upgrade-ubuntu-18-04-to-22-04/) to upgrade from Kubuntu 18.04 to 22.04 (it's for Ubuntu but I guess it's the same process).
It was working well, until I was asked what I wanted to do with a package, I think it was gnome (I forgot the path honestly, but it was something/gnome).
The prompt gave me about 5 different choices (if I wanted the releaser's version, the actual version, etc..) I don't really understand anything about that.
It also gave me the possibility to see the difference between the versions.. I thought I would have something I could understand, but no. I clicked enter to reach the end of file and I thought it would exit by itself, but it didn't, so I made the mistake to do **ctrl+z**.
The upgrade process was stopped. I tried the same command again, i.e.  **sudo do-release-upgrade **.
but it says:
**E: Could not get lock /var/lib/apt/lists/lock. It is held by process 17553 (focal)**
**N: Be aware that removing the lock file is not a solution and may break your system.**


I guess it's because the upgrade is still running in the background. 
I tried to reboot but failed (I didn't force it though), it said 

[B]Operation inhibited by "UpdateManager" (PID 17553 "focal", user root), reason is "Updating System".
Operation inhibited by "APT" (PID 1521 "focal", user root), reason is "APT is installing or removing packages".
Please retry operation after closing inhibitors and logging out other users.
Alternatively, ignore inhibitors and users with 'systemctl reboot -i'.[/B]

I don't want to force the computer to restart. Is there any hope I can resume the upgrade? It's been running for about 2 hours.

Thank you!

---

### Post by TheFu on 2022-10-12
cntl-z stops a process, but doesn't end it.  cntl-z is used normally to place a process into the background.  You need to learn shell "job control".

Typically, 
cntl-z <--- stops a running job and disconnects the input from the current terminal, 
then you'd be expected to enter 'bg' to place the stopped job into the background to continue.  This can be very useful, but not during an upgrade.  If you hadn't rebooted or closed that terminal window, you could have used the full 'job control' commands that are built into every shell to bring the job/task to the foreground again - 'fg' is the command.

To get a list of jobs under a current parent terminal session, the 'jobs' command is there.

jobs
fg
bg
cntl-z

That's pretty much it. The 'jobs' command will give a number to each job running, so you can specify 'fg 5' to bring task %5 to the foreground ... assuming there are at least 5 other jobs running under the terminal session.  Each terminal started from the GUI is a separate session, so the job control commands only work within 1 terminal.

As for the "new config file to be installed" stuff.  If you didn't change the config file, I always accept the new one recommended by the package installation.  If I did modify a config file, a) there will be a comment inside it to remind me, b) I'll look at the differences to decide if the 3 lines I touched are still important and need to be translated into the new version, c) If more than 3 lines are changed by me, I'll keep the old one and see if that causes problems or not.  

Perhaps most importantly, attempting an upgrade from 18.04 to 22.04 is a huge jump.  On KDE, the version of Qt changed in all those years, along with how networking and some other things are handled has completely changed.  I think that helping you to recover from the upgrade failure is going to end badly, so the best answer is to get your backups ready and perform a 100% fresh 22.04 KDE install.  This will leave you with a fresh, clean, OS ready for your data, settings, and fresh, clean installs of the extra programs you want.  

You did make a backup before starting right?  Before doing any upgrade ... and most patching (weekly), having a know-you-can-restore backup isn't just a nice to have. It is mandatory, unless you can live with extra downtime and updates that break your workflows.

---

### Post by stargazer4587 on 2022-10-12
Thank you very much. Alright then, it seems the best thing to do.


> **TheFu said:**
> cntl-z stops a process, but doesn't end it.  cntl-z is used normally to place a process into the background.  You need to learn shell "job control".

Typically, 
cntl-z <--- stops a running job and disconnects the input from the current terminal, 
then you'd be expected to enter 'bg' to place the stopped job into the background to continue.  This can be very useful, but not during an upgrade.  If you hadn't rebooted or closed that terminal window, you could have used the full 'job control' commands that are built into every shell to bring the job/task to the foreground again - 'fg' is the command.

To get a list of jobs under a current parent terminal session, the 'jobs' command is there.

jobs
fg
bg
cntl-z

That's pretty much it. The 'jobs' command will give a number to each job running, so you can specify 'fg 5' to bring task %5 to the foreground ... assuming there are at least 5 other jobs running under the terminal session.  Each terminal started from the GUI is a separate session, so the job control commands only work within 1 terminal.

As for the "new config file to be installed" stuff.  If you didn't change the config file, I always accept the new one recommended by the package installation.  If I did modify a config file, a) there will be a comment inside it to remind me, b) I'll look at the differences to decide if the 3 lines I touched are still important and need to be translated into the new version, c) If more than 3 lines are changed by me, I'll keep the old one and see if that causes problems or not.  

Perhaps most importantly, attempting an upgrade from 18.04 to 22.04 is a huge jump.  On KDE, the version of Qt changed in all those years, along with how networking and some other things are handled has completely changed.  I think that helping you to recover from the upgrade failure is going to end badly, so the best answer is to get your backups ready and perform a 100% fresh 22.04 KDE install.  This will leave you with a fresh, clean, OS ready for your data, settings, and fresh, clean installs of the extra programs you want.  

You did make a backup before starting right?  Before doing any upgrade ... and most patching (weekly), having a know-you-can-restore backup isn't just a nice to have. It is mandatory, unless you can live with extra downtime and updates that break your workflows.

---

### Post by TheFu on 2022-10-12
BTW, I use the jobs/fg/bg with multiple jobs maybe once every 3 yrs.  The 'fg {num}' is probably 'fg %{num}' ... but I don't really recall.  Looks like the %{num} is the way.  Sorry I don't really recall, since dealing with 1 job means not needing to know it.  I put things into the bg and pull them to the fg perhaps 5x a week.

[https://linuxcommand.org/lc3_lts0100.php](https://linuxcommand.org/lc3_lts0100.php) ... has examples.  BTW, I left off the 'kill' command.  Seems that 'kill %2' will find the 2nd task (use jobs to see which is which) and send a sigterm signal to kill it.

---

### Post by stargazer4587 on 2022-10-12
In case it helps anyone in the future, I forced my pc to restart. I found that Kubuntu 20.04 was installed, not 22.04.
There are a few things that don't seem right (no sound for example, a bit slow).
I tried to  upgrade to Kubuntu 22.04 and it asked me to do [B]sudo dpkg --configure -a

[/B]That's where I found myself right where I was, i.e. I had to choose between the 5 possibilities. I chose one and it's been running for a few minutes. If everything goes well, I'll upgrade it to Kubuntu 22.04.
Thanks again TheFu for your answers.

---

### Post by grahammechanical on 2022-10-12
> to upgrade from Kubuntu 18.04 to 22.04

We cannot do that whether we are running Ubuntu or one of its flavours such as Kubuntu. It is my understanding that we first upgrade from 18.04 to 20.04 and then upgrade from 20.04 to 22.04. 

Regards

---

### Post by TheFu on 2022-10-12
Even if the upgrade to 22.04 works, I think you'll have things that don't behave right and you'll be stuck with a not-so-great system.  Best to wipe, fresh install, restore your data and then restore the applications you need, as you come across the need again.  There are probably 15 apps you already know that you need. The other 100 are "cruft" for apps you used 1-2 times and never removed completely.

It is a pay me a little now vs pay me a bunch later thing.  Later might be this weekend or you might limp along for 6 months before bad things start happening that you can't figure out ... because we will assume that when you say 22.04, there isn't any cruft left behind.

---

