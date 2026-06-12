---
title: "totem-mozilla plugin volume"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vaskark on 2010-03-31
I'm using the totem-mozilla plugin for Firefox and whenever the plugin loads the volume is always muted by default. I guess I can see the wisdom of this but I'd really like to have the volume on by default. Does anyone know how to do this?

---

### Post by Shiba on 2010-04-01
Same here. It is a actually a problem here: [http://www.apple.com/it/findouthow/mac/#anatomy](http://www.apple.com/it/findouthow/mac/#anatomy)
Totem controls are disabled and I can't raise the volume at all. Btw, I'm not going to buy a mac :)

---

### Post by grandtoubab on 2010-04-01
Everything sound fine with gnome-mediaplayer and gecko-mediaplayer plugins :P

---

### Post by luke.varnadore on 2010-04-14
> **grandtoubab said:**
> Everything sound fine with gnome-mediaplayer and gecko-mediaplayer plugins :P

I second that. I think there is probably something goofy going on with the plugin that hasn't been addressed yet. gecko-mediaplayer works as expected.

---

### Post by bgruber on 2010-04-27
if the audio is set to mute and the totem plugin won't let you change it, that usually means there's something wrong and that it's unable to play the audio track for whatever reason.

on the other hand, i have a problem where the plugin's default volume is very low, and I have to adjust it every time a movie is loaded; sounds like the first poster on this thread has a similar problem where the default is to be muted. anyone have a fix for that?

---

### Post by neanderslob on 2010-04-28
@bgruber: Hey I have exactly the same problem but unfortunately no solution.  :guitar:

---

### Post by Milos_SD on 2010-04-28
I can't even play anything with Totem, and can't use gstreamer aplications for video. It try to find plugins (codecs), but it fails thare too. :(

---

### Post by simonxs on 2010-04-28
I have the same issue, video plays fine but no sound, although I can change it when I put it in fullscreen with the volume control. Sound works fine then but it doesn't stick when I load the next video. Sound is back to muted.

---

### Post by wilee-nilee on 2010-04-28
> **Milos_SD said:**
> I can't even play anything with Totem, and can't use gstreamer aplications for video. It try to find plugins (codecs), but it fails thare too. :(

Make sure the repositories in apt-get are on, then reload and look for ubuntu restricted extras in synaptic.

For those of you having problems with totem in genaral load the correct codecs as suggested above and install VLC or smpolayer  or any of the others mentioned in the thread, Totem has some limitations that can't be gotten past, at least by me.

---

### Post by Milos_SD on 2010-04-28
> **wilee-nilee said:**
> Make sure the repositories in apt-get are on, then reload and look for ubuntu restricted extras in synaptic.

For those of you having problems with totem in genaral load the correct codecs as suggested above and install VLC or smpolayer  or any of the others mentioned in the thread, Totem has some limitations that can't be gotten past, at least by me.

I have all gstreamer packages installed, and ubuntu restricted extras. Problem started when I updated(recompiled) ffmpeg from svn. It was manualy compiled before too, and totem and other gstremer apps worked, now it doesn't. Maybe that is not the problem, maybe it's something else, I don't know.
Is there a way to use mplayer to play apple trailers?

---

### Post by vredley on 2010-04-28
> **Milos_SD said:**
> Is there a way to use mplayer to play apple trailers?

Try gecko-mediaplayer.

---

### Post by wilee-nilee on 2010-04-28
> **Milos_SD said:**
> I have all gstreamer packages installed, and ubuntu restricted extras. Problem started when I updated(recompiled) ffmpeg from svn. It was manualy compiled before too, and totem and other gstremer apps worked, now it doesn't. Maybe that is not the problem, maybe it's something else, I don't know.
Is there a way to use mplayer to play apple trailers?

Give us a link so we can see if any that don't work may work for us. Also you may want to install vlc, mplayer is a bit deprecated there is a thread somewhere on the forums though about getting the best results from it.

---

### Post by rjcroy on 2010-04-29
This bug is in launchpad
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/527432](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/527432)

the fix is to type the following in a terminal

```
gconftool --type int --set /apps/totem/volume 100
```

---

### Post by simonxs on 2010-04-29
Sweet that worked rjcroy !! thank you  :) now it plays with sound without having to set it manually. Thanks

---

### Post by Milos_SD on 2010-04-29
> **wilee-nilee said:**
> Give us a link so we can see if any that don't work may work for us. Also you may want to install vlc, mplayer is a bit deprecated there is a thread somewhere on the forums though about getting the best results from it.

Non of the apple trailers works, and I can't play any video in totem (.avi, .mkv, .mpg, nothing).

---

### Post by simonxs on 2010-04-29
All the apple trailers works fine for me. They load up quite nice and sound plays fine. Although I did have to install Gnome Mplayer to make it work perfectly. I have chromium as a browser if that makes a difference.

---

