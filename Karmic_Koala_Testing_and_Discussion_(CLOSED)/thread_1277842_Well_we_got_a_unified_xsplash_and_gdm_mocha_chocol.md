---
title: "Well we got a unified xsplash and gdm mocha chocolate theme through to desktop"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-09-28
Not impressed at all. On my 22" lcd screen it looks horrid I'm afraid.

Boot time is exceptional and shutdown too, cant fault that at all.

---

### Post by Gourgi on 2009-09-28
> **philinux said:**
> On my 22" lcd screen it looks horrid I'm afraid.
same here :(

---

### Post by Squonk07 on 2009-09-28
Like the image or not (I agree that it's not really that great for LCD monitors), at least the action is smooth and that garish orange default background doesn't keep popping up in the middle and after the second throbber screen.

If I get bored with it I'll go ahead and change the background. It's supposed to be trivial to do so now.

EDIT: Already done so. The methodology seems to have changed slightly from the instructions offered [here]("http://ubuntuforums.org/showthread.php?t=1277030"). The GDM background (at least for me) is drawn from a different resolution version from the /usr/share/images/xsplash folder (not the same one as the xsplash). Since I have no idea which one it is, I just moved all the original brown ones into a separate folder and populated the /xsplash folder with renamed versions of my custom background. One of them was right.

---

### Post by oboedad55 on 2009-09-28
It's a real fugly shade of brown, isn't it? I'd be happy if I could play audio CDs, but still no love. Actually as I just checked, I can't play music at all. Nothing works in Rhythmbox or any other player.

---

### Post by mc4man on 2009-09-28
> Nothing works in Rhythmbox or any other player. 
Once you try to play an audio cd in rhythmbox any number of odd things *may* occur. 

Eject the audio cd, reboot and try again. On a straight a6 updated, all players other than rhythmbox i've tried play audio cd's fine ( used amarok, vlc and audacious.

The repo vlc doesn't seem to retrieve cd info, my built one on other install does

If you happen to get playback but no sound then click on volume control and move the slider a hair

---

### Post by oboedad55 on 2009-09-28
> **mc4man said:**
> Once you try to play an audio cd in rhythmbox any number of odd things *may* occur. 

Eject the audio cd, reboot and try again. On a straight a6 updated, all players other than rhythmbox i've tried play audio cd's fine ( used amarok, vlc and audacious.

The repo vlc doesn't seem to retrieve cd info, my built one on other install does

If you happen to get playback but no sound then click on volume control and move the slider a hair

I'll try again, but as I recall banshee caused the same problem so I assumed all players were funky. I hate amarok but I'll give it a try. Usually if I eject a CD I have to manually push the tray back in, the power button is useless and that's only with karmic.
Well, I gave amarok a try. No love there either. I can wait, it's still an alpha.

---

### Post by mc4man on 2009-09-29
Don't know banshee at all, so installed it. 
Seems to play local files fine, but as far as an audio cd gets hung up on retrieving the cd info metadata.

 It doesn't appear to want to play the cd until it does retrieve the track info which doesn't seem to be happening anytime soon.

It will import/play without the metadata

Maybe i'm not getting how to open an audio cd in banshee, but it seems straightforward and all suggests and recommends are installed.

On the other hand if I go to /home/.gvfs/cdda mount on scdX, open the folder, go edit -> select all, right click on one of the .wavs -> open with Banshee media player,it then loads and plays the tracks  from the cd fine (no info

---

### Post by oboedad55 on 2009-09-29
> **mc4man said:**
> Don't know banshee at all, so installed it. 
Seems to play local files fine, but as far as an audio cd gets hung up on retrieving the cd info metadata.

 It doesn't appear to want to play the cd until it does retrieve the track info which doesn't seem to be happening anytime soon.

It will import/play without the metadata

Maybe i'm not getting how to open an audio cd in banshee, but it seems straightforward and all suggests and recommends are installed.

On the other hand if I go to /home/.gvfs/cdda mount on scdX, open the folder, go edit -> select all, right click on one of the .wavs -> open with Banshee media player,it then loads and plays the tracks  from the cd fine (no info

What do you think is causing this? I assume it will be addressed sometime.

---

### Post by mc4man on 2009-09-29
> What do you think is causing this? I assume it will be addressed sometime.
probably best asked in a new thread if your inclined to, moving far off topic here.
If so, just lay out what happens, what banshee can and can't do

---

### Post by ffi on 2009-09-29
> **philinux said:**
> Not impressed at all. On my 22" lcd screen it looks horrid I'm afraid.

Boot time is exceptional and shutdown too, cant fault that at all.

I think it looks horrid on any screen/resolution it's just too brown and boring

---

### Post by oztrailrider on 2009-09-29
GDM itself has not changed for me. I have a new background that matches the xsplash background but GDM is still the same old grey. Is this what everyone else is seeing or is there a matching theme for GDM?.

---

### Post by philinux on 2009-09-29
Dont get me wrong I actually like the concept and the design.

I don't like the banding I'm seeing left and right in the gradient colour change. I know it's easy to change to a different image but we are talking about first impressions here.

---

### Post by NCLI on 2009-09-29
> **philinux said:**
> Dont get me wrong I actually like the concept and the design.

I don't like the banding I'm seeing left and right in the gradient colour change. I know it's easy to change to a different image but we are talking about first impressions here.
Please report this bug so it can be fixed before it's too late.

---

### Post by philinux on 2009-09-29
> **NCLI said:**
> Please report this bug so it can be fixed before it's too late.

Someone got there already. 
[https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/433034](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/433034)

---

