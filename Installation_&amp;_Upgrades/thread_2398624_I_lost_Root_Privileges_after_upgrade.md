---
title: "I lost Root Privileges after upgrade"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by webmiester on 2018-08-15
I am running Ubuntu mate 16.04 on a PC.

I wanted to do something with firefox but the firefox version I had on was too old.   So I did an uprage using sudo apt-get upgrade.

After sometime, I rebooted and my theme no longer exists, all my icons disappeared.  I can enter my Root Account on the GUI but when I try to click on things like >Administration>users, the system disallows me to manipulate anything.  It seems like my root account doesnt have root priveledges anymore.

Has anyone encountered this before?  Any suggestions?

---

### Post by Bashing-om on 2018-08-15
webmiester; Hello -

I take a stab at this - permissions ?

post back - between code tags - the out put of terminal command:
```

ls -al /home

```
as the place to start the looking.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]it's all in the process
[/INDENT]

---

### Post by webmiester on 2018-08-31
Thank you Bashing-om for your reply.

I was in a hurry to get this thing working so I just reflashed the harddisk with an image that was already prepared.  So I reverted back to the old ubuntu system, and I wont be upgreading it anymore.  Thanks

---

### Post by Bashing-om on 2018-08-31
webmiester; Hey - hey ")

Thanks for getting back and telling what you did for the resolution.
A nuclear solution always works --- good backups are a great thing to have !

As this situation is now concluded -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]ip up and away
[/INDENT][/INDENT]

---

