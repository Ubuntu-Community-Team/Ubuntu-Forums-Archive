---
title: "System &gt; Preference &gt; Sound Missing after latest panel updates"
date: 2009-07-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-07-16
As the title suggests... I was just getting around to tackling the various sound problems I've been experiencing in Karmic when I realized the menu option disappeared. It is also missing from gnome-control-center.

As for sound issues which seem ever-present in Ubuntu whether alpha, beta or release, I have only found issues relating to NO SOUND in Karmic. I am not experiencing that. I have sound when I watch video. I have sound when I listen to mp3's. I have sound in about 1/2 my games. My two main issues are:

1) Speakers crackle even on mute when new actions take place (e.g. adjust volume, launch gnome-terminal, system sounds), but not every time. This did not happen on Jaunty and I have modified absolutely nothing as far as config files hoping this would work itself out during the alphas as updates progress.

2) Sound is corrupt on certain games (e.g. wesnoth, ltris, frozen-bubble) yet works perfectly fine on others (supertux, gweled). Launching problematic games from terminal yields no errors to go by, so I am not sure where the root of the problem lies (pulseaudio, alsa, snd-hda-intel, ALC269, driver).

Having searched fruitlessly amongst the bazillions of threads concerning sound in Ubuntu, I hope someone here can shed light on both my original topic (missing menu items) and either of my main sound issues.

---

### Post by rtalcott on 2009-07-16
I noticed the missing control also..was just looking for it.

My sound and usb hardware has finally been recognized now that I installed the 2nd Alpha but my "big" problem is that I can see video from the Bloomberg stream but cannot get any audio....

rt

---

### Post by philinux on 2009-07-16
> **rtalcott said:**
> I noticed the missing control also..was just looking for it.

My sound and usb hardware has finally been recognized now that I installed the 2nd Alpha but my "big" problem is that I can see video from the Bloomberg stream but cannot get any audio....

rt

Just tried bloomberg and sound ok here. Annoying sound menu missing.

---

### Post by philinux on 2009-07-16
Just dipped in to jaunty. The launcher is gnome-sound-properties, maybe it's still there just not appearing in menus.

---

### Post by tekstr1der on 2009-07-16
Yeah, bloomberg stream works fine here too.

Fired up a VM of Jaunty and partially answered my original question. I appear to be missing gnome-sound-properties all together. Aptitude tells me to install gnome-control-center which is already latest version. A reinstall does not fix the issue. 

Is this by design? Should the launcher no longer be listed or do others still have it in their menus?

EDIT: You beat me to it philinux! My VM is slow!

---

### Post by rtalcott on 2009-07-16
Thanx...obviously the Bloomberg problem is MY problem!

And it does work fine for me on the 9.04 machines...guess I need to do some looking at config files....

KK has been remarkably problem free for me...

Thanx for checking the Bloomberg streams!
rt

---

### Post by chrisccoulson on 2009-07-16
The old gnome-sound-properties (System -> Preferences -> Sound) has been deprecated upstream for some time now, but we still built it in Ubuntu up until yesterday, when it was disabled in a gnome-control-center upload. 

gnome-volume-control-pulse is going to be merged back in to gnome-media over the next day or so, and System -> Preferences -> Sound will reappear as the newer Pulseaudio capplet instead.

---

### Post by tekstr1der on 2009-07-16
Thank you much. That's just the answer I was looking for. Now if only I can figure out the cause of my sound issues... Maybe a new thread for each!

---

### Post by Regenweald on 2009-07-17
The new volume control center is amazing, i just tested running smplayer and exaile simultaneously, muting, raising/lowering volume and such. All works perfectly. System sound is very low at maximum, but i don't have time to test right now. Outside of that I am very impressed :)

Looking forward to more updates.

---

### Post by dmn01 on 2009-07-17
What happens for those of us who don't run pulseaudio?  The loss of gnome-sound-properties seems to have disconnected my keyboard volume/mute keys from the gnome audio apps (but not from alsa).  How do I make the reconnection?

---

### Post by tekstr1der on 2009-07-17
> **Regenweald said:**
> The new volume control center is amazing...

I agree that the new sound preferences are nice. It's the first time the extra alert sounds have ever played for me. 

More importantly for me and my issues on topic, it gives me a glimpse of where my problems lie. On the Applications tab which shows what is outputting/inputting audio currently, when I play games with corrupt sound, it shows Asla flashing constantly in rhythm with the corruption. That's a lead anyway.

Does no one here have any similar sound issues in Karmic? I am very surprised at the lack of any me-too's or possible solutions.

---

### Post by durand on 2009-07-17
> **tekstr1der said:**
> I agree that the new sound preferences are nice. It's the first time the extra alert sounds have ever played for me. 

More importantly for me and my issues on topic, it gives me a glimpse of where my problems lie. On the Applications tab which shows what is outputting/inputting audio currently, when I play games with corrupt sound, it shows Asla flashing constantly in rhythm with the corruption. That's a lead anyway.

Does no one here have any similar sound issues in Karmic? I am very surprised at the lack of any me-too's or possible solutions.

Depends on the kind of games. I could never get stuff like Quake Wars (q4) to work but SDL games like tremulous (q3) work perfectly.

---

### Post by tekstr1der on 2009-07-17
Like I said in the OP, games such as wesnoth and frozen-bubble had working sound in previous Ubuntu versions, only since upgrade from Jaunty to Karmic alpha 2 have they been broken. Also you mentioned SDL above. sdlmame is experiencing the same broken up sound corruption here as well.

---

### Post by durand on 2009-07-17
> **tekstr1der said:**
> Like I said in the OP, games such as wesnoth and frozen-bubble had working sound in previous Ubuntu versions, only since upgrade from Jaunty to Karmic alpha 2 have they been broken. Also you mentioned SDL above. sdlmame is experiencing the same broken up sound corruption here as well.

Just tried frozen-bubble and the sound on that is terrible! I'm 100% sure it was working properly about a month ago.

---

### Post by yoasif on 2009-07-17
the frozen bubble thing might be [this bug]("https://bugs.launchpad.net/ubuntu/+source/frozen-bubble/+bug/386104"). report if the fix works for you. :)

---

### Post by durand on 2009-07-17
> **yoasif said:**
> the frozen bubble thing might be [this bug]("https://bugs.launchpad.net/ubuntu/+source/frozen-bubble/+bug/386104"). report if the fix works for you. :)

Did, thanks :D

---

### Post by rudenko_ruslan on 2009-07-17
I'm the only one who have 2 similar icons in tray? First icon is for "old" audio preferences, and the second is for "newer preferences".

---

### Post by chrisccoulson on 2009-07-17
> **rudenko_ruslan said:**
> I'm the only one who have 2 similar icons in tray? First icon is for "old" audio preferences, and the second is for "newer preferences".

That's because gnome-applets still ships the mixer-applet. I suspect that will be disabled at the next build, and will become a null applet and removed from your panel

---

### Post by tekstr1der on 2009-07-17
> **yoasif said:**
> the frozen bubble thing might be [this bug]("https://bugs.launchpad.net/ubuntu/+source/frozen-bubble/+bug/386104"). report if the fix works for you. :)

Wow! In one fell swoop all my game sound issues (wesnoth and sdlmame included) reported in the OP are fixed. Thank you so much for pointing this out.

---

### Post by durand on 2009-07-17
> **durand said:**
> Did, thanks :D

And I just noticed that my other games also run better! I used to think that they were graphics issues!

---

### Post by hanzomon4 on 2009-07-17
Screen Shot!

---

### Post by wayne_cat on 2009-07-17
> **hanzomon4 said:**
> Screen Shot!

```
root@macbook:~# Screen Shot!
No command 'Screen' found, did you mean:
 Command 'screen shot please' from package 'courtesy-tools' (main)
root@macbook:~# 

```:-k

---

### Post by hanzomon4 on 2009-07-17
> **wayne_cat said:**
> ```
root@macbook:~# Screen Shot!
No command 'Screen' found, did you mean:
 Command 'screen shot please' from package 'courtesy-tools' (main)
root@macbook:~# 

```:-k

No post a screenshot of the new sound applet/preferences.

---

### Post by wayne_cat on 2009-07-17
> **hanzomon4 said:**
> No post a screenshot of the new sound applet/preferences.

well ... if you read the complete error message ... maybe I will make a screen shot .. maybe

---

### Post by ghindo on 2009-07-18
> **hanzomon4 said:**
> Screen Shot!:)

---

### Post by hanzomon4 on 2009-07-18
> **wayne_cat said:**
> well ... if you read the complete error message ... maybe I will make a screen shot .. maybe

really?

> **ghindo said:**
> :)

Awesome thanks

---

### Post by tghe-retford on 2009-07-18
Still no SPDIF/IEC958 digital audio toggle in the new sound preferences, meaning users will have to install Pulseaudio Volume Control to turn on/off their digital audio. Updated existing bug for Karmic (when they tried to implement this into Jaunty):

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/317292](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/317292)

---

### Post by rudenko_ruslan on 2009-07-18
I found another interesting thing - volume level seems constantly setting "Output Volume" higher that 100%. It's not difficult to set it on 100%, but after playing next audio track, it sets "Output Volume" at 104% or 110% again.

Can anyone confirm this? Or it's just me...

---

### Post by amano on 2009-07-18
> **tghe-retford said:**
> Still no SPDIF/IEC958 digital audio toggle in the new sound preferences, meaning users will have to install Pulseaudio Volume Control to turn on/off their digital audio. Updated existing bug for Karmic (when they tried to implement this into Jaunty):

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/317292](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/317292)

I wonder, if that bug is present in Fedora as well? They released their latest and greatest with the new sound applet in May. :confused:

In my eyes it is rather a serious thing if there is no obvious way to turn on digital output in Karmic.

---

### Post by buzzmandt on 2009-07-18
> **rudenko_ruslan said:**
> I found another interesting thing - volume level seems constantly setting "Output Volume" higher that 100%. It's not difficult to set it on 100%, but after playing next audio track, it sets "Output Volume" at 104% or 110% again.

Can anyone confirm this? Or it's just me...
Not just you, my sound is rather unstable too.  especially when using vlc, it throws all the sound way out of proportion.  But even without vlc having ran I notice sound output kinda goes up and down at random

---

### Post by zika on 2009-07-19
Sound is, after boot, always on 0% and I have to run padevchooser to reset device at first run after boot also since it is on 0%. I'm running, through the session sound always on 100% so I do not see the reason it goes all the way down all the times ...

---

### Post by rudenko_ruslan on 2009-07-19
> **zika said:**
> Sound is, after boot, always on 0% and I have to run padevchooser to reset device at first run after boot also since it is on 0%. I'm running, through the session sound always on 100% so I do not see the reason it goes all the way down all the times ...
Yeah, I forgot to say about it in my previous post. Sound is muted at startup.

---

### Post by zika on 2009-07-19
> **rudenko_ruslan said:**
> Yeah, I forgot to say about it in my previous post. Sound is muted at startup.Huh, someone else ...

---

### Post by jerrylamos on 2009-07-19
> **zika said:**
> Huh, someone else ...
  

And someone else.  

Jerry

---

### Post by dagrump on 2009-07-19
My sound is muted at start up now, & to add insult to injury, I now have a second volume applet. Must have been the updates I did yesterday.
It appears one is master volume & the other is my sound card, very odd.

---

### Post by wayward4now on 2009-07-20
> **jerrylamos said:**
> And someone else.  

Jerry


Me too. It affects KDE as well. Ric:confused:

---

### Post by rudenko_ruslan on 2009-07-24
Most of the problems are fixed now (muted sound at startup, and duplicate icons). But there is still some mysterious thing happening with my Output Volume - something trying to set it higher, than 100%. I wonder, what can do that.

So, I want to ask testers - do you have the same problem (with output) with all current updates installed?

---

### Post by durand on 2009-07-24
Well, my sound output can only be below 0 dB. Is there a reason for this? If the actual output can't be established, shouldn't we just use a percentage unit instead?

---

