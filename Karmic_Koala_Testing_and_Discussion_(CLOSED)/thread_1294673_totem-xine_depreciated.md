---
title: "totem-xine depreciated?"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cor2y on 2009-10-18
I have just discovered that totem-xine along with totem-gstreamer seem to be dummy packages in karmic,
Now there is no decent dvd playback in karmic with the default media player.
Dont get me wrong totem with the gstreamer backend can handle regular multimedia playback but its lack of dvd menu navigation or sometimes selecting the correct dvd title to playback leaves a lot to be desired.
For the last few versions of ubuntu i have been trying to stick to one media player that does it all in 9.04 i had gotten it down to totem (with the xine backend) and mplayer (since vdpau for xine is not integrated as well as vdpau for mplayer).
Now it seems there is no more totem-xine. :(

---

### Post by kostkon on 2009-10-18
Yeap, it was deprecated in Gnome 2.28. But the good thing is that now Gstreamer has the ability to navigate DVD menus. ;)

---

### Post by mc4man on 2009-10-18
> but its lack of dvd menu navigation or sometimes selecting the correct dvd title to playback leaves a lot to be desired.

Plus here at least, it also doesn't parse the audio streams correctly.

While certainly not supported or to be "recommended" you can slot in a real totem-xine package based on the 2.26.1 source in place of the current dummy. As long as it remains compatible with the 2.28.X totem-common then it will work fine.

( noting that this would be as a 'standalone' local file and dvd media player, it can't replace the current 2.28.X totem as the default totem player (nor would you want it to.

I may rebuild when karmic releases and set it to the release version -1, though atm the -1 on the build from a few weeks ago is still keeping it 'higher'

---

### Post by kansasnoob on 2009-10-18
As someone that used Totem for watching movies I'm unhappy :cry:

VLC is just not quite "there".

That'll keep me on Jaunty for now.

Sorta makes me sad.

---

### Post by JEdwardP on 2009-10-25
I also use totem-xine because I'd found totem-gstreamer to have a serious problem with the audio of DVD's, but oddly, only CERTAIN DVD's.

---

### Post by kaibob on 2009-10-25
I was sorry to find that totem-xine was no longer available in the repo's. I tried mplayer, vlc, xine and a few others, but none of them seemed to work very well. This is still on my list of unresolved karmic issues. :(

---

