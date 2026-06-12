---
title: "Software Sources in System-&gt;Admin."
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2010-04-16
Since Software Sources can be accessed from both Software Center and Synaptic why do we have an entry for it in System->Admin.?
Seems kinda pointless? :confused:

---

### Post by ranch hand on 2010-04-16
Some of us actually like to configure the bugger before any other package management system is entered.

This is a good place to start if, for instance, you do not want Update Mangler endlessly harassing you to do partial upgrades.

I hit Software Sources just as fast as I can when booting into a new install for the first time.

---

### Post by Slug71 on 2010-04-16
Isn't Software Center integrating Software Sources anyway though?

---

### Post by ranch hand on 2010-04-16
You know there are people that do not use Software Center or Synaptic or any other gui at all for package management.

---

### Post by cariboo on 2010-04-16
To me the Software Center is looking better all the time, but it still feels unfinished, it doesn't provide the information I expect, like when updating repositories, or if there are new packages in the repositories. I'll reserve my judgement until it is done, but so far I still use Synaptic.

---

### Post by ranch hand on 2010-04-16
I have software center on my panel along with terminal and synaptic.  SC is getting less and less use.

---

### Post by JoeWheeler on 2010-04-16
I don't use software centre.

If i know what I'm trying to get I just use command line else I use synaptic

---

### Post by Atermoon on 2010-04-16
I actually use it only from the system menu. Can't even remember the last time I opened synaptic or software center and it wasn't for installing something, that's for sure.
Aptitude ftw :)

---

### Post by mc4man on 2010-04-16
> Since Software Sources can be accessed from both Software Center and Synaptic why do we have an entry for it in System->Admin.?
Seems kinda pointless?

Possibly for visibility - in sc it's in 'edit', synaptic in 'settings'

(while sc seems to be progressing nicely, because of it's layout it will never be as useful as synaptic's for certain tasks

---

### Post by zekopeko on 2010-04-16
> **ranch hand said:**
> You know there are people that do not use Software Center or Synaptic or any other gui at all for package management.

Those people can then edit by hand /etc/apt/sources.list

---

### Post by zekopeko on 2010-04-16
> **cariboo907 said:**
> To me the Software Center is looking better all the time, but it still feels unfinished, it doesn't provide the information I expect, like when updating repositories, or if there are new packages in the repositories. I'll reserve my judgement until it is done, but so far I still use Synaptic.

I've actually started to use USC almost exclusively. It still has ways to go but its starting to look really nice. They could do amazing things in presenting software with it.

---

### Post by Slug71 on 2010-04-16
> **cariboo907 said:**
> To me the Software Center is looking better all the time, but it still feels unfinished, it doesn't provide the information I expect, like when updating repositories, or if there are new packages in the repositories. I'll reserve my judgement until it is done, but so far I still use Synaptic.

Agreed. I think and do the same.

---

### Post by Slug71 on 2010-04-16
> **zekopeko said:**
> Those people can then edit by hand /etc/apt/sources.list

Agreed.

---

### Post by ranch hand on 2010-04-16
> **zekopeko said:**
> Those people can then edit by hand /etc/apt/sources.list
Yes they can.  They can't, there, stop the check for daily updates which is, to me, important.

I update the the list on all my testing installs in as short a time window as I can (chroot).  I then upgrade 2 of them as a test of the upgrade.  If it is good, and some stupid program has not changed the update list, I can do that upgrade anytime.

I like to turn that off before it gets a chance to start so the first thing I do when logging in for he first time is head directly to Software Sources and uncheck that box and reboot.  I know of no other way to do that which may be due to simple ignorance.  If I knew another that I could do by chroot, I would do it before logging in even once.

I also know of no other way to enable the popularity option although it is not done in the /etc/apt/sources.list.

---

### Post by tommynz1975 on 2010-04-16
Is it wishful thinking or reality??

In terminal

sudo apt-get update && sudo apt-get dist-upgrade 
work a lot faster than in the gui.

---

### Post by ranch hand on 2010-04-16
> **tommynz1975 said:**
> Is it wishful thinking or reality??

In terminal

sudo apt-get update && sudo apt-get dist-upgrade 
work a lot faster than in the gui.
+397
A lot faster.

---

### Post by Seventh Reign on 2010-04-16
> **cariboo907 said:**
> To me the Software Center is looking better all the time, but it still feels unfinished, it doesn't provide the information I expect, like when updating repositories, or if there are new packages in the repositories. I'll reserve my judgement until it is done, but so far I still use Synaptic.

It is improving steadily.  The problem is for every step forward, Canonical jumps backwards about 5 steps.

---

### Post by cariboo on 2010-04-17
> **tommynz1975 said:**
> Is it wishful thinking or reality??

In terminal

sudo apt-get update && sudo apt-get dist-upgrade 
work a lot faster than in the gui.

Aptitude? see screenshot. :)

---

### Post by ranch hand on 2010-04-17
I do not even like aptitude.  It is a lot better than SC is ever going to be.

---

### Post by Mr. Picklesworth on 2010-04-17
> **ranch hand said:**
> I do not even like aptitude.  It is a lot better than SC is ever going to be.

Better ... ?

---

### Post by ranch hand on 2010-04-17
Yes, easier and to find stuff in, easier to use, faster to use.

Some may think that SC looks better.

I think the term we are looking for here is "aptitude is better than SC will ever be".

---

### Post by seeker5528 on 2010-04-17
> **zekopeko said:**
> Those people can then edit by hand /etc/apt/sources.list

By that logic, we shouldn't have the option to change the wallpaper when we right click the desktop.

Why have a link there when we can go to 'System --> Preferences --> Appearance --> Background'? 

After all people who don't want to mess with that can just open a terminal window and do:

```
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/path/to/some/image.png"
```

Later, Seeker

---

### Post by seeker5528 on 2010-04-17
> **ranch hand said:**
> I think the term we are looking for here is "aptitude is better than SC will ever be".

<SHUDDER>

AKA 'Jelous **** that doesn't like you using other utilities behind her back'. :shock::twisted:

Personally if I'm going the CLI route and want something more convenient than using dpkg and/or apt-get directly, I'll stick with aptsh.

Maybe that's just me.:P

Later, Seeker

---

