---
title: "No Sound in 9.10 (Karmic)"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Exodist on 2009-10-24
Is anyone else having any sound issues on 9.10. 
I have a SB Audigy2 and every thing seems to be setup correctly. But for some reason the new sound manager isnt spitting out any sound. I am assigned to the Sound/Audio groups. 

Any thoughts?

---

### Post by RichardLinx on 2009-10-24
I haven't tested Karmic but it might be that sound is just muted, have you checked in sound preferences? I don't know why but this happened to me when I tried Ubuntu 8.04 out a long time ago.

Most likely though, Pulse Audio is the culprit. Remove pulse audio and install esound.

Edit: Here's how: [http://ubuntuforums.org/showpost.php?p=8139087&postcount=2](http://ubuntuforums.org/showpost.php?p=8139087&postcount=2)

---

### Post by Exodist on 2009-10-24
I wish it was that simple :-(

It does act like the sound is muted and totem plays music and it shows up under the pulse audio control dialog box. But no sound. System sound also does not play. I prob should check launchpad for any listings on this issue and get it reported asap. But then again I had similar issues in 9.04 when using KDE unless I installed Gnome first.
So I check my ownerships to see if I was in Audio/Sound etc.. Good to go there.
So this isn't looking promising, all the new features to be plagued with an existing bug is sad. Looks like Pulse audio still needs to be removed until the devs can collaborate with the lead developer of Pulse and get this road smoothed out.

- Exo

---

### Post by Reaved on 2009-10-24
I also have a nonfunctional Audigy 2 and I've been testing and upgrading Karmic since about Alpha 5. When I first installed Karmic the audio did not work but I was able to get it working.  That was up until about 1-2 days ago when an upgrade broke it.

Unfortunately I didn't bookmark the instructions but if I can find them again and they work as before I will post them.  I seem to remember needing to delete an audio related config file and do an audio system restart.  Wish I could be more specific.

---

### Post by Reaved on 2009-10-24
Okay, I have gotten mine to work again by running alsamixer in a terminal, move right until you find the "Audigy A" control and hit M to unmute it.

Hope this works for you as well. :-\"

---

### Post by Exodist on 2009-10-25
Thanks for the input Reaved. 
I also have built in 7.somthing audio on my mobo. It works great. Since I am not gaming anymore I removed the Audigy2. Sadly it now works. SB cards *should* be the most compatible of all cards..

Also if you could post in Launchpad what you did to fix the issue maybe they can get a fix in for the initial release this week.

- Exo

---

