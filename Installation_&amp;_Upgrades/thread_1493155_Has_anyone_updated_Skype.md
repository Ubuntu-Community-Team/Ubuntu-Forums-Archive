---
title: "Has anyone updated Skype?"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by anonSam on 2010-05-25
For the first time ever I see an update for Skype in SPM. Does anyone know if this update breaks the search function like they did for Windows? I'm using version v2.1.0.47. Only thing SPM says:

Changes for the versions:
2.1.0.47-1
2.1.0.81-1ubuntu4

---

### Post by lisati on 2010-05-25
> **anonSam said:**
> For the first time ever I see an update for Skype in SPM. Does anyone know if this update breaks the search function like they did for Windows? I'm using version v2.1.0.47. Only thing SPM says:

Changes for the versions:
2.1.0.47-1
2.1.0.81-1ubuntu4

I noticed and updated. Haven't noticed any problems so far. Then again, I don't use Skype that much.....

---

### Post by wieman01 on 2010-05-25
Upgraded, no problems whatsoever. Camera, sound, micro.

---

### Post by anonSam on 2010-05-25
Okay, sounds good, but what I really want to know is if you still have the function to "Search for other users in Skype-me mode" (when they are in Skype-me mode, not myself). A while ago the Windows update quietly made this feature disappear (probably due to abuse), but they still left the Skype-me mode available. I love meeting and chatting with (somewhat) random people from other countries. If this feature is gone, I'll probably stop using Skype because I wouldn't be able to meet anyone on it.

---

### Post by dBz on 2010-05-26
It doesn't work all that well for me.  Specifically, many of the notification sounds don't make any sound, neither when the event happens, or when I click on "Test Event" in the relevant options window.

Some of the broken ones include:

Skype Login
Skype Logout
Skype Login Failed
Incoming Call Ringing (which is pretty annoying)
and all of the Chat sounds.

Most of the others do work (like outgoing calls) and I can make a very clear call to the Skype Test Call service so it's not a fundamental sound issue.  Just an issue with some notifications.

Is the old version still available?  Synaptic reckons 2.1.0.81 is the only available version, but I'd really like to back it out (unless somebody can suggest a fix).

---

### Post by walt11 on 2010-05-27
[SIZE=2]dBz, I'm having the same problem that you are, but it's not due to the update in my case. I've received 2 updates since originally installing Skype a couple of weeks ago, and this problem has persisted in all 3 versions. (I'm currently also on 2.1.0.81, and Ubuntu 10.04.)

I think the problem may be more global than just in Skype. E.g., I have Evolution set to play a sound when new mail arrives, but I'm not getting it.
[/SIZE]

---

### Post by dBz on 2010-06-03
Turns out Skype produces two kinds of sounds:  Output and Events.  All my Output sounds were working, but none of my Event sounds.  That turned out to be because I had them set to muted in the system-wide sound settings.

System->Preferences->Sound->SoundEffects:  Alert volume

Un-muting them gives me all my skype sounds.

dBz.

---

### Post by walt11 on 2010-06-03
[SIZE=2]Thanks dBz. You pointed me to the right place. My sounds were not muted, but the Alert volume was set too low. By appropriately setting the Output volume, Alert volume, and the volume control on my speakers, I'm getting about the right levels, and all the Skype sounds. I appreciate the help.[/SIZE]

---

### Post by brookie on 2010-06-04
Thanks! Alert volume? Who woulda thought? 
Unmuting alert volume did the trick. Took me forever to find a fix for this. :)

---

