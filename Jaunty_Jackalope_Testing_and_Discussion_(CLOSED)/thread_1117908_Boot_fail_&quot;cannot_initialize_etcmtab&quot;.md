---
title: "Boot fail &quot;cannot initialize /etc/mtab&quot;"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mikeize on 2009-04-06
Aaargh!  I had a system lockup today (normal occurrence through since 7.10?)--and I did REISUB to restart.  Ubuntu failed to reboot.  The first error I can see on the screen is "Cannot initialize /etc/mtab"  and then a bunch of other "permission denied" errors for init.d?.  I'm using a livecd right now, and I looked at my /etc/mtab file, but I really don't know what I'm looking for.  Someone help please!

*edit* Solved it with a re-install.  :p

---

### Post by bluemarble on 2009-04-20
I have the same problem and I hope I dont need to reinstall to solve the problem...

I have found few similar posts but none have ever had a response... I guess its a problem no one likes to talk about :)

If anyone has some suggestions, help is appreciated!

---

### Post by mikeize on 2009-04-21
Good luck, and please post back if you find a good solution.  I've had to reinstall 2 or 3 times now because of this problem.  On the bright side, I have been forced to learn a bit about backing up!  Having your /home on it's own partition is a no-brainer, but backing up your installed programs is a little more in-depth.  Aptoncd didn't work very well for me, and neither did sbackup.  I ended up using some dpkg commands which I forget right now, but should be easy to find with google.  For what it's worth, it seems like this problem occurred after using REISUB to restart after a lockup.  For now, I'm just using the power button.

---

