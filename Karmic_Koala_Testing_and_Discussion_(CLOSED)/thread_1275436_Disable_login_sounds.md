---
title: "Disable login sounds"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Longinus00 on 2009-09-25
Is there anyway to disable the drum sound on bootup? In the old gdm you could turn it off in the login preferences, but now that the login preferences has been neutered how would I go about doing this?

---

### Post by Crushyerbones on 2009-09-28
I need some help too. I find that sound HIGHLY annoying.

---

### Post by riskbreaker927 on 2009-09-28
Thirded.

---

### Post by fuzzyk.k on 2009-09-28
Me too, and i prefer the old gdm manager

---

### Post by mdurham on 2009-09-28
See the following, I think it's being worked on.

gnome-volume-control is missing system events sound adjustment
[https://bugs.launchpad.net/bugs/324700](https://bugs.launchpad.net/bugs/324700)

---

### Post by mannheim on 2009-09-28
> **mdurham said:**
> See the following, I think it's being worked on.

gnome-volume-control is missing system events sound adjustment
[https://bugs.launchpad.net/bugs/324700](https://bugs.launchpad.net/bugs/324700)

There are two different issues here. The above bug is about the login sound (and other system sounds): the login sound referred to there is the sound that you hear **after** logging in.

But **before** logging in, there's the sharp drumming sound from gdm, which is what this thread is about, I think. You used to be able to turn it off in the login preferences (gdm setup). If this isn't configurable, then karmic is going to be quite unusable for many people: no one is going to take their laptop to the library or classroom if it makes that noise every time the login screen appears.

---

### Post by tjeremiah on 2009-09-28
i think if u lower the alert sound, it effects the drum.

---

### Post by zika on 2009-09-28
Someone with a spare time shoud examine if some of these commands could be useful for the problem that bugs us all ... [http://ubuntuforums.org/showpost.php?p=8014635&postcount=500](http://ubuntuforums.org/showpost.php?p=8014635&postcount=500)

---

### Post by Crushyerbones on 2009-09-28
I had to use ubuntu during a class today (I forgot to bring along some printed papers) and the sound scared the crap out of everyone :(

---

### Post by froggyswamp on 2009-09-28
Same here, but putting this issue aside, common, how can one put a sharp drumming sound (at login)? really. Sorry, but the first thing an intelligent person would care doing - is making sure the sound is soft and pleasant, no phd is required to understand such simple things. I understand and respect Canonical's commitment to the African roots, but let's still stay wise and put user experience in first place.

---

### Post by andrewabc on 2009-09-28
I'm on Jaunty and in system->preferences->sounds tab-> I can customize the sound. They better allow it in Karmic.

---

### Post by cororok on 2009-09-28
yes. it's annoying me too.

---

### Post by Longinus00 on 2009-09-28
> **froggyswamp said:**
> Same here, but putting this issue aside, common, how can one put a sharp drumming sound (at login)? really. Sorry, but the first thing an intelligent person would care doing - is making sure the sound is soft and pleasant, no phd is required to understand such simple things. I understand and respect Canonical's commitment to the African roots, but let's still stay wise and put user experience in first place.

I don't know about you but I think hearing the windows sound at 100% volume on crappy laptop speakers that are being overdriven sounds as bad as the ubuntu login sound when you're in a library or during a lecture.

---

### Post by rburkartjo on 2009-09-28
froggy well said

---

### Post by Crushyerbones on 2009-09-28
> **Longinus00 said:**
> I don't know about you but I think hearing the windows sound at 100% volume on crappy laptop speakers that are being overdriven sounds as bad as the ubuntu login sound when you're in a library or during a lecture.


Well but at least you can disable the windows sound... :(

---

### Post by zika on 2009-09-28
> **Crushyerbones said:**
> Well but at least you can disable the windows sound... :(You can turn off or down sound on the laptop too ...

---

### Post by Aearenda on 2009-09-28
Of course, Karmic is not yet ready for 'production' use in the classroom - you should be using Jaunty there!

I find this sound very annoying too.  I expect this will be controllable in the GUI by the time Karmic is released.

The sound that is played is the one linked at /usr/share/sounds/ubuntu/stereo/system-ready.ogg.

---

### Post by cororok on 2009-09-28
> **Aearenda said:**
> Of course, Karmic is not yet ready for 'production' use in the classroom - you should be using Jaunty there!

I find this sound very annoying too.  I expect this will be controllable in the GUI by the time Karmic is released.

The sound that is played is the one linked at /usr/share/sounds/ubuntu/stereo/system-ready.ogg.

Ok. I simply relink it like
sudo ln -s dialog-information.ogg system-ready.ogg

---

### Post by BoyOfDestiny on 2009-09-28
> **Aearenda said:**
> Of course, Karmic is not yet ready for 'production' use in the classroom - you should be using Jaunty there!

I find this sound very annoying too.  I expect this will be controllable in the GUI by the time Karmic is released.

The sound that is played is the one linked at /usr/share/sounds/ubuntu/stereo/system-ready.ogg.

Cheers for that. It's going to replaced with a "silence" version courtesy of audacity... ;)

---

### Post by fuzzyk.k on 2009-09-29
check the tenth tread in the post think it might help with the sound
[post]("http://ubuntuforums.org/showthread.php?t=1277846")

---

### Post by Longinus00 on 2009-09-29
> **fuzzyk.k said:**
> check the tenth tread in the post think it might help with the sound
[post]("http://ubuntuforums.org/showthread.php?t=1277846")

> Unticking Gnome Login Sound in Preferences > Startup Applications should stop it.

Because that's obvious to the average user. They really ought to change how they expose that functionality.

---

### Post by Aearenda on 2009-09-29
> Unticking Gnome Login Sound in Preferences > Startup Applications should stop it. 
I think that's the 'logged in' sound, not the 'ready to log in' sound.

---

### Post by meborc on 2009-09-29
UGLY FIX - buy cheap headphones... cut off the jack... stick it in... the end!

---

### Post by bluenova on 2009-09-29
> **Longinus00 said:**
> I don't know about you but I think hearing the windows sound at 100% volume on crappy laptop speakers that are being overdriven sounds as bad as the ubuntu login sound when you're in a library or during a lecture.

Someone always has to bring Windows into the discussion. So you're saying it's ok for Ubuntu to have anoying startup sounds because MS Windows does? I don't follow your logic.

---

### Post by Crushyerbones on 2009-09-29
> **Aearenda said:**
> I think that's the 'logged in' sound, not the 'ready to log in' sound.

Confirmed. I've never even had it on in the first place.

---

### Post by Longinus00 on 2009-09-29
> **bluenova said:**
> Someone always has to bring Windows into the discussion. So you're saying it's ok for Ubuntu to have anoying startup sounds because MS Windows does? I don't follow your logic.

My point was that a loud sound when unexpected is going to be annoying no matter what the sound is.

---

### Post by jatatar on 2009-09-30
i just deleted the sounds all together...i never liked them, so who cares really.

from the directory /usr/share/sounds/ubuntu/stereo

sudo rm system* 

and for login sounds

sudo rm desktop*

---

### Post by zika on 2009-09-30
> **jatatar said:**
> i just deleted the sounds all together...i never liked them, so who cares really.

from the directory /usr/share/sounds/ubuntu/stereo

sudo rm system* 

and for login sounds

sudo rm desktop*Or (simply) rename them ...?

---

### Post by meborc on 2009-09-30
but this is not a proper fix... there has to be a "tick" somewhere...

---

### Post by tophatandy on 2009-10-08
about 20 days left until the release, and there is no real way to silence a startup sound?

Someone should make a new bug and get it triaged properly, because its looking like something that probably isn't going to happen within those 20 days otherwise..

---

### Post by Aearenda on 2009-10-08
It's [already there]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429"). Doesn't look promising.

---

### Post by taavikko on 2009-10-08
Quick workaround...
```
sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
```

---

### Post by Aearenda on 2009-10-08
Good workaround, taavikko - much better than the sound file hacks!

---

### Post by zika on 2009-10-08
Bad news is that I had to reinstall. Good news is that there is no login sound when turned off in Karmic (fully upgraded). It is relict that did not get corrected through upgrades.

---

### Post by emarkay on 2009-10-08
Added my "vote" to the Bug!

---

### Post by emarkay on 2009-10-12
Looks like another bug filed - one of these will be marked "dupe".
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700)
original:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429)

---

### Post by autocrosser on 2009-10-12
Ubuntu-sounds update this morning to all who hack (me included)--I sub another sound file in there (Star Trek--awaiting Command codes ;)  ).....So remember to re-hack after....

---

### Post by Wtwine on 2009-10-19
Go to System/Administration/Login Window and click on "Accessibility".  Disable "Login screen ready" by unchecking the box. That will remove the irritating bongo drum sound at the login prompt.  :)

---

### Post by biji on 2009-10-19
hahah i thought it was only me who annoyed to that drum sound :D

---

### Post by CbrPad on 2009-10-19
> **Wtwine said:**
> Go to System/Administration/Login Window and click on "Accessibility".  Disable "Login screen ready" by unchecking the box. That will remove the irritating bongo drum sound at the login prompt.  :)

Hmm, I don't have that option.  I only have "Show the screen for choosing who will log in" or "Log in as xxx automatically".

---

### Post by tekstr1der on 2009-10-19
> **Wtwine said:**
> Go to System/Administration/Login Window and click on "Accessibility".  Disable "Login screen ready" by unchecking the box. That will remove the irritating bongo drum sound at the login prompt.  :)

Are you referring to the configuration options for the old GDM? The new options are very limited.

No one has figured out how to stop just the bongos through the UI? Looks like the workaround by taavikko is the best yet.

---

### Post by cyberkilla on 2009-10-19
> **tekstr1der said:**
> Are you referring to the configuration options for the old GDM? The new options are very limited.

No one has figured out how to stop just the bongos through the UI? Looks like the workaround by taavikko is the best yet.

[COLOR="Silver"]There is an entry to disable a "sound plug-in" in GDM in gconf-editor.[/COLOR]

EDIT: Doesn't matter, I've tried it and I can't get it to shut up. It must have been a fluke that it worked last time:)

EDIT #2: I wouldn't care half as much if the damned drum roll didn't appear a good three seconds before the login box appeared;)

---

