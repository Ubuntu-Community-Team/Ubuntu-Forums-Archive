---
title: "No shutdown/logout menu"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zengeos on 2010-04-14
Over the last day I seem to be encountering an odd problem.

Initially, my logout/shutdown menu had disappeared.

I loaded Update Manager this morning, hoping it might fix the problem
No go.

Tonight, I checked Update Manager and was prompted to do Partial Upgrade, which I proceeded to do.
Now, not only is the Logout/shutdown menu gone, but my notification icons, namely Network Connectivity, now ook like white noise on a television screen.

Any suggestions to try?

Thanks-

---

### Post by ranch hand on 2010-04-14
Log out using the terminal.

Don't do partial upgrades.

---

### Post by bluestar14 on 2010-04-14
probably wouldn't be partial if you did Alt-F2, and typed in 
```
update-manager -d
```

---

### Post by ranch hand on 2010-04-14
I think that you both better read the stick at the top of every menu page on this forum;

[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

The first post is the only one you need to read, it won't hurt you a bit.  It may save you further problems.

The command that bluestar14 is recommending is for upgrading from a previous version of Ubuntu.  Do not do this for updates, it is not a good idea.

---

### Post by cariboo on 2010-04-14
To get your on/off button back, reinstall fast-user-switch-applet, you would probably be just as well off installing the rest of the notification applets. I would suggest you use Synaptic Package Manager to do you updates, as it won't do any partial upgrades, like update manager does. I would also suggest you read the stickies at the top of this page, as they contain valuable information.

---

### Post by zengeos on 2010-04-14
Odd,

I read though several of the sticke posts at the top but nothing struck me as pertaining to this. Must have missed it.

Thanks, will reperuse.

---

### Post by bluestar14 on 2010-04-14
oh, sorry for giving invalid advice!

---

### Post by bluestar14 on 2010-04-14
> **ranch hand said:**
> I think that you both better read the stick at the top of every menu page on this forum;

[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

The first post is the only one you need to read, it won't hurt you a bit.  It may save you further problems.

The command that bluestar14 is recommending is for upgrading from a previous version of Ubuntu.  Do not do this for updates, it is not a good idea.

oh, sorry for giving invalid advice!

---

### Post by zengeos on 2010-04-14
By the way, the lack of logout menu was an issue prior to Partial Upgrade. I had HOPED, perhaps without merit, that the patial upgrade might actually offer a correction to the missing logout menu.  Since it included, primarily, an incremental linux update, I allowed the partial upgrade to occur.

Ahh well.

say la.

---

### Post by zengeos on 2010-04-14
aptitude is indicating I have unmet dependencies, specifically gdm

aptitude says I have the latest gdm installed.

So, I cannot install or upgrade fast-user-switch-applet.

Cariboo, I think you found the problem for me, thanks.

Any other suggestions for things to try in oder to fix the issue?

---

### Post by zengeos on 2010-04-14
terminal restart seems to have corrected things for the time being, at least.  Not sure why the restart after partial upgrade didn't fix it though. Oh well.  Beta is now back to it's normally smooth operation.

Thanks all for the suggestions.

Appreciated.

mark-

---

