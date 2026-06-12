---
title: "Can't do update because of wrong hash code"
date: 2023-03-05
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2023-03-05
Installed kubuntu a few years ago (maybe 2-3 years) on a newer computer.  Hash was correct and updates were possible at the beginning.  Now can't do updates anymore, because of wrong hash code.  But still get update notices which slows down the computer.   What to do now. Reinstall? The same can still happen. How can  the hash become inccorrect later?

---

### Post by Bashing-om on 2023-03-05
bjngchn; Hello

> 
How can the hash become inccorrect later?


Things change - corruption can happen.

Show us the error that you see >> post back the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade

```

so we see the error in context.

[INDENT]one step forward
[/INDENT]

---

### Post by bjngchn on 2023-03-06
[FONT=monospace][COLOR=#000000]command: 
[/COLOR][/FONT]sudo apt update[FONT=monospace][COLOR=#000000]

output:[/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]Hit:1 [http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu) focal InRelease [/COLOR]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease                                         
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB][COLOR=#b26818]                        [/COLOR][COLOR=#000000] [/COLOR]
Hit:4 [http://ppa.launchpad.net/xtradeb/apps/ubuntu](http://ppa.launchpad.net/xtradeb/apps/ubuntu) focal InRelease              
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB][COLOR=#b26818]     [/COLOR][COLOR=#000000] [/COLOR]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease [108 kB] 
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [59.9 kB]
...etc...and..[/FONT]
Reading package lists... Done [/COLOR]
Building dependency tree        
Reading state information... Done 
67 packages can be upgraded. Run 'apt list --upgradable' to see them.

It happened fast. No errors. Strange, in th past it would install lots of things. 
..........
Didn't try the second one : 
[/FONT]sudo apt upgrade

because I don't want an upgrade.
.....
In the past I would do:
sudo apt-get update
Looks like the result would be the same as the first command,
although the last time I tried it would give hash error.

[FONT=monospace]
So it looks like, there is no change since then except that there is no error anymore,
nothing is done but no error given either. 
[/FONT]

---

### Post by deadflowr on 2023-03-06
Why don't you want to update the packages?

---

### Post by Bashing-om on 2023-03-06
Agobjngchn Gey hey ....

> 
because I don't want an upgrade.


^^ too) in my opinion such conduct is unwise. Just this past week we have 111 unique CVEs addressed with 17 vulnerabilities that promote new kernels.
Best practice is keep the system updated.

[INDENT]A bad day can happen quickly
[/INDENT]

---

### Post by bjngchn on 2023-03-13
Update ok, upgrade not.

---

### Post by oldos2er on 2023-03-16
```
sudo apt upgrade
``` updates or upgrades (a lot of people, including me, may use those words interchangeably) currently installed packages. ```
sudo apt full-upgrade
``` updates currently installed packages, and may also ```
intelligently handles
           changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution
           system, and it will attempt to upgrade the most important packages at the expense of less
           important ones if necessary. The dist-upgrade command may therefore remove some packages.
``` (quote from apt-get's man page). Neither apt upgrade nor apt-full-upgrade will upgrade you to a newer OS version.

If you post the exact hash error it would help people to help you.

---

