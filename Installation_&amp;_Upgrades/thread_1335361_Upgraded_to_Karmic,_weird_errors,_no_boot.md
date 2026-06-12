---
title: "Upgraded to Karmic, weird errors, no boot"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by otz070 on 2009-11-23
First thing I noticed when I first restarted after the upgrade was this:

"inotify_add_watch" then a bunch of whatever then "bad address"

came up about 10 or so times in a row. Then took a while to load something about unable to mount partition or something...

It loaded sucessfully the first two times, then after I restarted from fixing the settings it messed up, it crapped out on me.

now it does as stated above, except instead of loading the login screen, I get to a black screen with the blinking "_" 

Tried running recovery, the same thing comes up (the inotify thing)
then I go into the GUI and if I try to go to dpkg or anything at all, the screen gets all screwed up. Like parts of it are here and there. (text where things shouldn't be, like if a graphics card has an error sometimes I guess.)

Later on I'll post more detailed descriptions, (its a bit hard for me, I have one keyboard for 2 computers, have to unplug and switch.)

Any ways if anyone has any suggestions on how to fix this (not clean install either, or switch to windows.) I'd like to find an actual solution please, thank you;)

---

### Post by cariboo on 2009-11-23
Have you tried running:

```
apt-get -f install
```

from the recovery prompt, to make sure you have completed the upgrade?

---

### Post by otz070 on 2009-11-29
if I let it alone for awhile, sometimes it runs, and sometimes it fails. Also audio is completely gone. 

As per the command given, didn't really help much.

Got it to load into the desktop the other day, and this morning it failed.
Right now its on the black screen, with

```
*Reloading Common Unix Printing System: cupsd
```

And its like its frozen there.

Seems like it fails to boot completely when I don't have the keyboard plugged in.

Either way, I still have the "inotify" errors comming up, and the audio issue. (Found out about the audio issue the other day on a sucessful boot)

I also when it freezes on boot, when I force it to quit, one of the "*" is red. I'll post what that is later, I think that one is somehow related to audio.

Anyways thanks;)


I'm on that one right now

It booted (more or less) properly after I plugged the keyboard in. Is there a way to fix it so I can use keyboardless boot like with the older versions? (I have to share 1 keyboard between two computers, this one I don't really need a keyboard for as I just use it for a music player.)

Error with after the red "*"
```
Pidfile not found is Jackd running?
```

I'll run an update in a few minutes here to see if it fixes anything. (with any luck it will)

Thanks again.

---

### Post by otz070 on 2009-12-06
Ok found a solution, just noticed I was still on the old kernal.
Had problems getting it to upgrade though. (Packages held back) fortunatly I found this helpful little command command:

```
sudo aptitude dist-upgrade
```
Just in case anyone else has trouble like I had.

Fixed most everything, audio is back too.

---

