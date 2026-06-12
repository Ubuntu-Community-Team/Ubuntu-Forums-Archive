---
title: "Accidentally clicked &quot;Keep Obsolete Packages&quot; During Upgrade from 13.10 to 14.04"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by joseph11h on 2014-05-06
Like the title says, I had finished upgrading a family member's Ubuntu system to 14.04 today, and when I got to the last step, I somehow accidentally clicked "Keep Obsolete Packages". I want to get rid of these. It said there were like 80 or so obsolete packages, I think?

I did:
sudo apt-get autoremove

after I rebooted the computer, and it only removed 4 packages. Is there a terminal command, or a way through the package manager, to remove these obsolete packages I meant to get rid of?

I'm really stumped here, and I hate to spend half a day re-installing from scratch, because I had a lot of extra programs and extra repositories installed on this particular machine.

Can anyone give me a hint? I found this thread, [http://ubuntuforums.org/showthread.php?t=1328596](http://ubuntuforums.org/showthread.php?t=1328596) and they did the same thing I tried, with autoremove, and it fixed it for this person, but this was back in 2009. Like I said, in my instance, there were ~80 obsolete packages to be removed, and autoremove only removed ~5.

Any suggestions? Does anyone know how to get rid of these obsolete packages leftover from my upgrade to 14.04? Help is very much appreciated, and I'll mark the thread as "SOLVED" as soon as I get an answer that does it. I might even tip some Bitcoin if you are extra helpful :) since I don't see this issue addressed anywhere online.

-joseph11h

---

### Post by Bashing-om on 2014-05-06
joseph11h; Hi !

Try this approach, and pay attention to the outputs.
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
dpkg --configure -a

```
Which should remove any un-needed files and also resolve any unmet dependency issues. This is the "deep" house cleaning in 'buntu. There should be nothing else required.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

