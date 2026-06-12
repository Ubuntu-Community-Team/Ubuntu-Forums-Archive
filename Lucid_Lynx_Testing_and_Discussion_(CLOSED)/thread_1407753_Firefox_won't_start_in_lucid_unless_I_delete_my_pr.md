---
title: "Firefox won't start in lucid unless I delete my profile"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hexion on 2010-02-15
I've been using Linux for years, always the development version since I use Ubuntu.. and I can honestly say this is the weirdest issue I've ever had.

I have 2 system partitions, one with karmic and the other one with lucid. Both share the /home partition. When I boot into lucid, I cannot start firefox. No errors in console, just won't start. If I boot into karmic I can start it. That's not too weird..

Now, if I remove ~/.mozilla/firefox in my lucid session, Firefox will start fine. Hmm.. weird.
If I now close and try to reopen firefox, it won't work... weirder.
Now I go there and delete my profile folder again, and I can open firefox again.

At the first moment I thought of apparmor messing around so I checked the configuration and couldn't figure out any difference (other than the version) with that in karmic.


Any ideas?

---

### Post by lovinglinux on 2010-02-15
Perhaps is because you are sharing the home partition between both installations.

---

### Post by mdurham on 2010-02-15
Do you access the profile (or home partition) via a link? It won't work for me if accessed that way.
If you're interested, bug report is [here]("https://bugs.launchpad.net/bugs/517903")

---

### Post by hexion on 2010-02-15
> **lovinglinux said:**
> Perhaps is because you are sharing the home partition between both installations.
The fact that this is reproducible when I create a new profile, denies your hypothesis. The new profile contains no trace of the other environment.

Plus I tested with a clean upgrade too.

---

### Post by hexion on 2010-02-15
> **mdurham said:**
> Do you access the profile (or home partition) via a link? It won't work for me if accessed that way.
If you're interested, bug report is [her]("https://bugs.launchpad.net/bugs/517903")[e]("https://bugs.launchpad.net/bugs/517903")
No links involved, the partition is mounted normally.

I'm not affected by that bug since in my case even brand new profiles hit the issue too. Thanks anyway!

---

### Post by lovinglinux on 2010-02-15
> **hexion said:**
> The fact that this is reproducible when I create a new profile, denies your hypothesis. The new profile contains no trace of the other environment.

But the ~/.mozilla folder is still shared and could have permission issues. I know now is not the case.

> **hexion said:**
> Plus I tested with a clean upgrade too.

OK.


Try to start Firefox with this command:

```
firefox -P "default"
```

Where "default" (with quotes) is your Firefox profile name.

---

### Post by trulan on 2010-02-15
Hey!  I'm in Firefox in Lucid for the first time since late December!  Deleting my profile fixed it right up!
[http://ubuntuforums.org/showthread.php?t=1366283](http://ubuntuforums.org/showthread.php?t=1366283)
Here's a thread I started back then, I seemed to be the only one with the issue.  The problem persisted and I installed Chromium.  And after reading your thread and deleting my profile, firefox started right up.  I'll have to close things and see if the problem re-appears.

I have messed around with chroot a few times but my installations do not share home folders.

---

### Post by lovinglinux on 2010-02-15
> **trulan said:**
> Hey!  I'm in Firefox in Lucid for the first time since late December!  Deleting my profile fixed it right up!
[http://ubuntuforums.org/showthread.php?t=1366283](http://ubuntuforums.org/showthread.php?t=1366283)
Here's a thread I started back then, I seemed to be the only one with the issue.  The problem persisted and I installed Chromium.  And after reading your thread and deleting my profile, firefox started right up.  I'll have to close things and see if the problem re-appears.

I have messed around with chroot a few times but my installations do not share home folders.

Check other tips on my tutorial [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by hexion on 2010-02-15
I'm not sure where did I read it, but the culprit was the file "compatibility.ini"!!!

If I delete that file, I can start firefox again! Although firefox will create it again so if I close it I will need to delete it in order to start it again.

Well, at least I can script it as a workaround. I'll open a bug now!

---

### Post by hexion on 2010-02-15
For those who have the same issue and would like to workaround it:

> sudo vi /usr/lib/firefox-3.6/firefox.shOr gedit, or nano, whatever file editor..

Then at the beginning, after the variable definitions, add these lines and save:
```
COMPATIBILITY_FILE="$MOZDIR/$META_NAME/**YOUR_PROFILE_FOLDER_NAME_HERE**/compatibility.ini"
[ -f "$COMPATIBILITY_FILE" ] && rm "$COMPATIBILITY_FILE"
```That'll do!

---

### Post by trulan on 2010-02-16
Cool - but deleting the profile fixed mine right up - must have been a different problem...but thanks anyway, you were instrumental in fixing my problem.  And thanks too, LL, for the link.  Good stuff.

---

### Post by wylzee on 2010-02-19
removing compability.ini fixed it for me too, thanks

---

### Post by jfernyhough on 2010-02-19
Just thought I'd throw in another possible workaround.

Start firefox -safe-mode, quit. then start firefox normally. Worked for me for the last year. Perhaps I should have found a solution. :D I'll try the compatibility.ini thing now (though I might just make an empty file and mark it readonly).

--edit
Nope, that just disabled all of my extensions! (I'm running 3.7a2pre). Delete it instead!

---

