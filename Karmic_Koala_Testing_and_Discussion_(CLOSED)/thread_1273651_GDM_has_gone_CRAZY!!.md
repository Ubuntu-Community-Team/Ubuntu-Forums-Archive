---
title: "GDM has gone CRAZY!!"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by qwerty800 on 2009-09-23
Basically, GDM crashes for some reason at boot (The messages are going too fast, don't have the time to read anything).

Symptoms: It cause the screen to flicker, and don't stop displaying something like:
> gmd has performed an illegal operation, terminating.
gdm has been terminated, respawning
gmd has performed an illegal operation, terminating.
gdm has been terminated, respawning
gmd has performed an illegal operation, terminating.
gdm has been terminated, respawning
... 
:lolflag:

Well, these are all the details I can get for now. I'm currently runing on a LiveUSB of jaunty.

Thanks in advance!:)

---

### Post by novafluxx on 2009-09-23
boot to recovery mode, run apt-get update and apt-get upgrade

---

### Post by qwerty800 on 2009-09-23
Even trough the recovery mode's main console is quite (a lot) buggy, I managed to update, upgrade and dist-upgrade, but it still don't work.

---

### Post by qwerty800 on 2009-09-23
I'm upping this, hoping to get an awnser soon...

---

### Post by qwerty800 on 2009-09-24
Help, please! :(

---

### Post by qwerty800 on 2009-09-24
Is it really that hard to get help?

I SWEAR that, if I manage to get out of this, Karmic is my last pre-release EVER.

---

### Post by qwerty800 on 2009-09-24
Man, I think I'll soon have more "up"s than there is of relases of Ubuntu if nobody answer me...

---

### Post by cariboo on 2009-09-24
Please don't bump threads more than once every 24 hours. If people to many posts in a thread, they may think you are getting help and bypass your thread.

---

### Post by ranch hand on 2009-09-24
I think you need to do three things.

One - remember that this is an alpha release.  I truly hope this is not on a production box.

Two - keep updating and upgrading.  I do not think that a dist-upgrade is that great an idea in your case.

Three - it is awful hard to guess at your problem with no information.  What in flinderation do you have this installed on?  Some info would really help.

I, for instance have had some problems with the gdm.  It seems to be good now.  This was caused by the video card that I have (ATI).  People can not be expected to know what you are using.

The folks here on the forums are users like you.  We do this because someone has helped us in the past and we try to pass that on.  Demands for help, particularly with no details, will not get yu very far.

When you installed 9.10 and at the top of every menu page on this forum (testing) you are warned that this is "**Karmic Koala Testing and Discussion**
 [B]Ubuntu Karmic Koala is in development, use only for testing purposes!!!"


[/B]

---

### Post by TerminX on 2009-09-25
This happened to me as well.  What's happening is for some reason or another, X isn't starting and gdm is just respawning over and over instead of whatever failover sort of crap it's supposed to do.

I "fixed" it by booting into single user mode, removing the respawn line from /etc/init/gdm.conf and then booting up normally and fixing the issue preventing X from starting in the first place.

---

### Post by qwerty800 on 2009-09-25
@TerminX:

Yeah, dude, you're awesome!! Look, I'm kissing you right now:P!!

It was because I had uninstalled my Nvidia drivers to replace them by nouveau (I don't know what I was thinking back then), and it looks like X.org didn't took that in account.

But it works now, hurray!!:popcorn:

Hope this may help somebody else!

---

