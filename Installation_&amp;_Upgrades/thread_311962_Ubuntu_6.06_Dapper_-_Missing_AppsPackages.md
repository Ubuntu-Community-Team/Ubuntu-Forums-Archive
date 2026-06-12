---
title: "Ubuntu 6.06 Dapper - Missing Apps/Packages"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by three-cushion on 2006-12-03
My Ubuntu installed OK (Mac OS 10.4.8 1GB ram, 800MHZ HW). System updates arrive regularly and update correctly. Firefox and Evolution work even tho I have one IP for mail in and the DSL IP for mail out! Here are my most vexing problems

1) Add/Remove, and Software Preferences does not work.
When I launch these, after they has searched for apps installed, they QUIT and disappear. 

2) Short of a long and tedious Ubuntu re-install, any ideas how to retreive these two features?

Without SW Pref, how am I ever going to allow Universal updates?

Specifically, I have a 95% install of clamav but can't get the rest due to libclam1 missing and the virual libgmp3?

Synaptic Mgr does work OK.

Cheers, Jim B

---

### Post by mssever on 2006-12-03
> **three-cushion said:**
> My Ubuntu installed OK (Mac OS 10.4.8 1GB ram, 800MHZ HW). System updates arrive regularly and update correctly. Firefox and Evolution work even tho I have one IP for mail in and the DSL IP for mail out! Here are my most vexing problems

1) Add/Remove, and Software Preferences does not work.
When I launch these, after they has searched for apps installed, they QUIT and disappear. 

2) Short of a long and tedious Ubuntu re-install, any ideas how to retreive these two features?

Without SW Pref, how am I ever going to allow Universal updates?

Specifically, I have a 95% install of clamav but can't get the rest due to libclam1 missing and the virual libgmp3?

Synaptic Mgr does work OK.

Cheers, Jim B
As far as Add/Remove goes, if you run it from a terminal (by typing gnome-app-install), you might get some error messages to help diagnose the problem.

I'm not sure what you mean by software preferences or universal updates, but you can do everything that Add/Remove can do and a lot more in Synaptic. And the system will pariodically check for updates and notify you of them. If you still can't install them through your favorite method, you can use Synaptic or various command-line tools.

Also, if you haven't put too much time yet into tweaking your Ubuntu install, re-installing might be easier than troubleshooting--depending on your Linux skill level, of course.

---

### Post by three-cushion on 2006-12-04
> **three-cushion said:**
> My Ubuntu installed OK (Mac OS 10.4.8 1GB ram, 800MHZ HW). System updates arrive regularly and update correctly. Firefox and Evolution work even tho I have one IP for mail in and the DSL IP for mail out! Here are my most vexing problems

1) Add/Remove, and Software Preferences does not work.
When I launch these, after they has searched for apps installed, they QUIT and disappear. 

2) Short of a long and tedious Ubuntu re-install, any ideas how to retreive these two features?

Without SW Pref, how am I ever going to allow Universal updates?

Specifically, I have a 95% install of clamav but can't get the rest due to libclam1 missing and the virual libgmp3?

Synaptic Mgr does work OK.

Cheers, Jim B
[I]As far as Add/Remove goes, if you run it from a terminal (by typing gnome-app-install), you might get some error messages to help diagnose the problem.

I'm not sure what you mean by software preferences or universal updates, but you can do everything that Add/Remove can do and a lot more in Synaptic. And the system will pariodically check for updates and notify you of them. If you still can't install them through your favorite method, you can use Synaptic or various command-line tools.

Also, if you haven't put too much time yet into tweaking your Ubuntu install, re-installing might be easier than troubleshooting--depending on your Linux skill level, of course.
__________________[/I]

Sorry... I meant "Software Repositories"  Don't I need thenm to open up the Universal repositories? Like clamav...

Also, for a re-install... can that be done wothout starting over with the 'liveCD'?

If so, where can I find a procedure to follow. I think I have enuff rudimentary skills (UNIX, mostly) to do it.  EG, is there the equivalent to Apple's Combo release(s) that might work? Or, is there a way to extract what I need from the 'LiveCD'?

Thanks for your prompt reply....

Cheers, Jim B 
PS I'll try your Add/Removal idea

---

### Post by mssever on 2006-12-04
> **three-cushion said:**
> Sorry... I meant "Software Repositories"  Don't I need thenm to open up the Universal repositories? Like clamav...

Also, for a re-install... can that be done wothout starting over with the 'liveCD'?

If so, where can I find a procedure to follow. I think I have enuff rudimentary skills (UNIX, mostly) to do it.  EG, is there the equivalent to Apple's Combo release(s) that might work? Or, is there a way to extract what I need from the 'LiveCD'?

Thanks for your prompt reply....

Cheers, Jim B 
PS I'll try your Add/Removal idea

The repositories are set in /etc/apt/sources.list. Just uncomment the universe repos, then do a ```
sudo apt-get update
``` Alternately, in Synaptic you can go to Settings > Reposities.

When it comes to a reinstall, it's probably possible to do it without using the LiveCD, but I wouldn't know how to help you there. You'd probably have to do a fair amount of Googling. In short, I don't know if it would be worth the trouble. And I'm not a Mac user, so I don't know what a combo release is.

---

