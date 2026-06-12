---
title: "Fubared screen on first login"
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by Ste on 2005-02-18
Ubuntu installs fine, then when it goes to start the gdm the screen goes mad. Examples shown below.

The second picture being the last point in the ubuntu installation before it attempts to login to the gdm.

Further point, I recently got a new 80GB HD and since then this has happened. Didn't have a prob on the old 20GB drive. And I get the same error from VLOS 1.1 installation but Mandrake 10.0 and Suse 9.2 install fine, but I want Ubuntu more than anything else.

[img]http://www.audioarch.co.uk/Images/ubuntu_crash1.jpg[/img]
[img]http://www.audioarch.co.uk/Images/ubuntu_crash2.jpg[/img]
[img]http://www.audioarch.co.uk/Images/ubuntu_crash3.jpg[/img]
[img]http://www.audioarch.co.uk/Images/ubuntu_crash4.jpg[/img]

---

### Post by Ste on 2005-02-18
Could I boot knoppix and change the sources.list to wartys and try that ?
I installed knoopix to the HD last night and worked fine till I dist-upgraded and libxv1 wouldn't let me apt-get anything else so I installed Suse over it. 
Would I overwrite sources.list while booting the cd-rom or when it's installed on the HD ?

---

### Post by wulf on 2005-02-18
Interesting. Is the system still responding (eg. can you turn the caps lock and num lock keys on and off?). If so, it might be worth trying Ctrl-Alt-Backspace to restart X. On my laptop it sometimes finishes booting and then, instead of showing GDM, the screen goes white. This happens maybe half the times I boot up but is normally easily fixed with Ctrl-Alt-Backspace.

It's a bit of a pain but it's not very predictable and I haven't been able to discern any trace of it in the log files. Your problem might be completely different but a three finger salute would be easy to try (plus I'd like to hear of other people having a similar problem to me ;) - the more witnesses, the more chance the bug will be caught).

Wulf

---

### Post by Ste on 2005-02-18
Strange thing is I can still move the mouse around but ctrl-alt-backspace dosnt work neither does ctrl-alt and the F keys, so it results in a cold reset from me.
Very annoying.
It's also a dekstop not a laptop so I'm stumped. The fact it happened with another distro leads me to believe it's not a ubuntu problem but then why will some distros install and ubuntu won't ? Ubuntu being the one I want to run.

It's a cruel world.

---

### Post by Ste on 2005-02-18
Problem solved, turns out there was a bad block in one of the partitonm tables.
Must have been when I first put XP on the disk.
Had the PC open trying to copy over files from the 20GB disk when I tried Disc Image from 2002, which told me the info I needed. Norton Ghost wasn't as helpfull.

Now back to Ubuntu goodness, Oh HAPPY DAYS!

---

