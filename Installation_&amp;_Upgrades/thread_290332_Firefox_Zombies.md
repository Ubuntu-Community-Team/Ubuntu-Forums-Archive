---
title: "Firefox Zombies"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by wdbreen on 2006-11-01
Gday All,
Upgraded to edgy last week and have been using firefox 2.0 as my browser.
I have noticed that each time it starts up, it leaves behind a zombie process called [netstat] <defunct>.
Is this anything to worry about and does anybody else get this?

Breeny

---

### Post by nacho on 2006-11-26
I noticed the same on my system (fresh install of Edgy on AMD64).

user    5478     1  5 22:05 ?        00:00:59 /usr/lib/firefox/firefox-bin
user    5497  5478  0 22:06 ?        00:00:00 [netstat] <defunct>

// Jesper

---

### Post by sh4d3z on 2006-12-13
same here... i'm using xfce dapper drake though...with ff 2 
it's alway the same pid too 5660
i was told to kill nautilus in fc forums... but it said no process killed, i run ps aux again and it still there... is this night of the living dead or what? kill -SIGKILL 5660 doesn't work

---

### Post by sh4d3z on 2006-12-13
hmmm after shutting down ff the zombie was killed and i have reopened it and run the ps -aux and i still see no zombies so this might have worked 
killall nautilus
then restart ff...
or
kill -SIGKILL <pid of the zombie>
or just kill -9 <pid of the zombie>
and restart ff
or maybe it was both and restart ff... i'll check this out again when i reboot and keep yall up to date
this is a bug that other users of different distros are expriencing as well obviously... do a google on [netstat] <defunct> and see for yourself
-nic

---

### Post by sh4d3z on 2006-12-13
okay... it appears i have to repeat this process erytime i login on xfce session, surely there is a more permanent fix

---

### Post by Technikal on 2007-01-27
I figured out a way around this problem, edit the firefox launcher to pass firefox %u --sync and that should stop the zombie process from being spawned. I did this earlier and haven't had any zombies since.

 - Technikal

---

