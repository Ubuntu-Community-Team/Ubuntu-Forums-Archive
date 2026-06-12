---
title: "Snap : How does that work exactly ?"
date: 2024-10-22
forum: Installation &amp; Upgrades
---

### Post by georgesgiralt on 2024-10-22
Hi Guys, 
On one machine, I ran "snap refresh".
This gave me this output : 
```
snap refresh
core20 20240911 from Canonical&#10003; refreshed
root@menfin:~# snap list
Nom                        Version                     Révision  Suivi            Éditeur        Notes
bare                       1.0                         5         latest/stable    canonical&#10003;     base
canonical-livepatch        10.9.0                      286       latest/stable    canonical&#10003;     -
chromium                   130.0.6723.58               2980      latest/stable    canonical&#10003;     -
core                       16-2.61.4-20240607          17200     latest/stable    canonical&#10003;     core
core18                     20240920                    2846      latest/stable    canonical&#10003;     base
core20                     20240911                    2434      latest/stable    canonical&#10003;     base
............... 
```
On another machine, I get 
```
snap refresh
Tous les paquets Snaps sont à jour.
root@espineux:~# 
root@espineux:~# 
root@espineux:~# snap list
Nom                        Version                     Révision  Suivi            Éditeur        Notes
bare                       1.0                         5         latest/stable    canonical&#10003;     base
canonical-livepatch        10.9.0                      286       latest/stable    canonical&#10003;     -
chromium                   129.0.6668.100              2972      latest/stable    canonical&#10003;     -
core                       16-2.61.4-20240607          17200     latest/stable    canonical&#10003;     core
core18                     20240920                    2846      latest/stable    canonical&#10003;     base
core20                     20240705                    2379      latest/stable    canonical&#10003;     base
.... 
```
As you can see, the core20 package is not up to date but is not "refreshed". 
Both machine run the same Ubuntu Noble version with all packages up to date but obviously snaps are somewhat broken... 
If I do this : 
```
snap refresh --list
Name      Version        Rev   Size   Publisher   Notes
chromium  130.0.6723.58  2980  180MB  canonical&#10003;  -

```
we can see that Chromium will be, one day, updated, maybe, but that core20 is not due to refresh ???? 
I can't understand why and how to manage snap packages and update them. I've read, many times, the man page for snap command and, I'm still very very confused. 
P.S. How could I get chromium updated as it is running all the time ? And why is it not updated when running ? ?? ?
Many thanks in advance for your help ! 
HAve a nice day !

---

### Post by grahammechanical on 2024-10-22
The Snap package method makes it possible to put out upgraded versions of software sooner than with the Debian packaged method of software which has to have a code audit. We should keep in mind that even when the snap package is maintained by Canonical employees these people will be in different teams. They have different work loads. 

Regards

---

### Post by georgesgiralt on 2024-10-22
But how do you explain that in one computer snaps are updated and not on the other ? 
And how come a snap package is not upgraded when the app is running ? 
Also, the snap-store gives a warning about it's needed update but can't be updated...
Something is very very wrong with this snap system. Even if they may be advantage to it (and I doubt it), it is not properly designed nor implemented.

---

### Post by davetheoldcoder on 2024-10-23
Here's a comprehensive reference on Snap: [https://snapcraft.io/](https://snapcraft.io/)

It has a forum where you can ask questions: [https://forum.snapcraft.io/](https://forum.snapcraft.io/)

---

### Post by grahammechanical on 2024-10-23
> Also, the snap-store gives a warning about it's needed update but can't be updated...

It is my guess that that message is there for corporate user who never turn off their machines or close applications and who update/upgrade to a schedule.

> Even if they may be advantage to it (and I doubt it), it is not properly designed nor implemented. 				

Everything in Linux is a work in progress. It is customary to release code (applications) as soon as they are working (after a fashion). It allows the user to be a tester and report bugs. This is the way things go in Linux. Some years ago Canonical came up with the ides of teaming up Canonical developers with community programmers to produce software that would not be released until it was finished and polished.

Canonical was accused of being secretive and there was an excessive amount of insults aimed at Canonical and its owner. So, the idea was dropped. Now, we are still in the situation where software is released when it works after a fashion but it becomes fully featured and polished over time.

Get used to it or stay with Microsoft or Apple.

Regards

---

### Post by georgesgiralt on 2024-10-24
> **grahammechanical said:**
> It is my guess that that message is there for corporate user who never turn off their machines or close applications and who update/upgrade to a schedule.


Well, sincce I retired, I turn my computer off every night to save power. And snaps are not updated neither at shutdown nor power up. And, in case of the snap-store, it can't be updated if you do not kill it beforehand... 
> 
Everything in Linux is a work in progress. It is customary to release code (applications) as soon as they are working (after a fashion). It allows the user to be a tester and report bugs. This is the way things go in Linux. Some years ago Canonical came up with the ides of teaming up Canonical developers with community programmers to produce software that would not be released until it was finished and polished.

Canonical was accused of being secretive and there was an excessive amount of insults aimed at Canonical and its owner. So, the idea was dropped. Now, we are still in the situation where software is released when it works after a fashion but it becomes fully featured and polished over time.

Get used to it or stay with Microsoft or Apple.

Regards
I've actually more than 50 years of experience in Unixes (some of them you never knew they existed) It is using either Microsoft or Apple product that I'm not confident with. But  entropy is increasing, at very very fast pace.  And Linux is not exempt from this. Fancy behaviour and or strange bugs show.
Of course we have these fancy round corners on our windows and the choice of colours for items in our menus but still the state of the desktop is not saved when you log out or poweroff.... And that would be a more than most wanted bug fix existing since the early century. 
We still suffer the Microsoft Empire because young people had been crafted using their products and when they decide to turn their aim at Linux, when a Linux app or feature is close to a Windows behaviour, they deem it acceptable... 
I think the snap problem not able to actually update an app when it is running is here to stay because the whole rationale behind snaps impose it. This is what I do not understand with snaps. Why was it not seen nor thought that update would be nearly impossible when the early design came out ?  
Yes, I know, entropy is increasing and people focus on only one point at a time nowadays (and that includes me) .... But some evolution are not bad. For example see the bin, lib, sbin merge in /usr. This is something Unixes should have done in the 90's... So I'm still confident someday snaps will be user friendly and upgradable...  Will I see it ? I don't know.

---

