---
title: "Weird behaviour of Intrepid 8.10 Alpha 2"
date: 2008-07-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Liakath on 2008-07-15
Dear Friends,

I have installed Alpha2 version on my Desktop (the specs are in my signature) through alternate CD downloaded. I have a few problems running it.

1. It does not allow me to use NVIDIA display package; When I try to install SYNAPTIC wants to remove a large number of installed packages.
I am able to use it under 1024*768 resolution which is native to my SAMSUNG SyncMaster 510N 15" LCD; but unable to activate desktop effects.

2. I am not able to see any of the splash screens during boot up; Only a block screen which ends up with GDM login manager. I have enabled boot splash through Startup Manager.

3. I am unable to retain running programs after reboot; I have used System>Preferences>Sessions to remember the running applications. But still has no effect.

Did any one who has installed has similar problems who could help in setting up my system optimally.

---

### Post by Sef on 2008-07-15
Moved to Intrepid Ibex Testing.

---

### Post by psyke83 on 2008-07-15
> **Liakath said:**
> 1. It does not allow me to use NVIDIA display package; When I try to install SYNAPTIC wants to remove a large number of installed packages.
I am able to use it under 1024*768 resolution which is native to my SAMSUNG SyncMaster 510N 15" LCD; but unable to activate desktop effects.

There have been major changes to the packaging of NVIDIA drivers in Intrepid. You only need to search this subforum for the term "nvidia" and check the half-dozen threads already discussing this topic.

Also, if the NVIDIA driver isn't installed, how could compiz (Desktop Effects) possibly work? Get the proper driver installed first.

> 2. I am not able to see any of the splash screens during boot up; Only a block screen which ends up with GDM login manager. I have enabled boot splash through Startup Manager.

That's a known issue, though you didn't need to enable anything.

> 3. I am unable to retain running programs after reboot; I have used System>Preferences>Sessions to remember the running applications. But still has no effect.

I'm not sure about that one. GDM was recently updated, so it could be a new bug that was introduced.

Please, search this forum before posting issues like these. You have a 90% chance of finding answers to questions like these by performing a simple search, and it'll save time for *you* and anyone else that replies to duplicate issues.

---

### Post by caryb on 2008-07-15
> There have been major changes to the packaging of NVIDIA drivers in Intrepid. You only need to search this subforum for the term "nvidia" and check the half-dozen threads already discussing this topic.


I would give the guy the benefit of the doubt because this post was moved from somewhere else.


Cary

---

### Post by psyke83 on 2008-07-15
> **caryb said:**
> I would give the guy the benefit of the doubt because this post was moved from somewhere else.


Cary

Sure. You have to admit that this happens a lot in this forum, though, so I said what was on my mind in the hope that others may think of doing a search before posting (it actually takes less energy to do a search compared to composing a new post :)).

What would be really nice would be a sticky thread (or perhaps even better, a user-editable page on the wiki) listing "general notes" and daily issues" affecting Intrepid. For example: "usplash isn't working, see bug #xxxxxx, see workaround at xxx", "sound is not working due to PulseAudio incorrectly selecting snd_pcsp as the default PCM device, see ...", "the restricted drivers manager is not ready"... yadda yadda. It would help everyone focus, contribute and confirm bugs faster, and generally make things a lot better for everyone.

---

### Post by Liakath on 2008-07-15
Dear psyke83,

I appreciate your remarks.

> **psyke83 said:**
> Sure. You have to admit that this happens a lot in this forum, though, so I said what was on my mind in the hope that others may think of doing a search before posting (it actually takes less energy to do a search compared to composing a new post :)).

What would be really nice would be a sticky thread (or perhaps even better, a user-editable page on the wiki) listing "general notes" and daily issues" affecting Intrepid. For example: "usplash isn't working, see bug #xxxxxx, see workaround at xxx", "sound is not working due to PulseAudio incorrectly selecting snd_pcsp as the default PCM device, see ...", "the restricted drivers manager is not ready"... yadda yadda. It would help everyone focus, contribute and confirm bugs faster, and generally make things a lot better for everyone.

Probably the sticky's as suggested would be really help.

---

### Post by caryb on 2008-07-15
+1 & maybe a link to any workarounds!


Cary

---

### Post by ronacc on 2008-07-21
> **Liakath said:**
> Dear Friends,



3. I am unable to retain running programs after reboot; I have used System>Preferences>Sessions to remember the running applications. But still has no effect.

Did any one who has installed has similar problems who could help in setting up my system optimally.


I filed bug # 249265 on this

---

### Post by Liakath on 2008-07-22
Dear Folks,

I could solve the problem of NVIDIA using my earlier xorg.conf file from hardy which also had the right monitor setup (SAMSUNG SyncMaster 510N)

But problem 2 of no splash screen still bugs me with no solution.

Problem 3 of sessions not being remembered still continues. Hope the bug report filed helps

Liakath

---

