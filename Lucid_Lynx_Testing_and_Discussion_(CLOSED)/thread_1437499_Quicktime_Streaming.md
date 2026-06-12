---
title: "Quicktime Streaming"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dropknee on 2010-03-24
I can't view quicktime movies, like apple trailers page. I have all the plugins required to make this work, but really don't know why I still getting the download quicktime advice in apple page.

Any Help??


Thanks

---

### Post by Rob2687 on 2010-03-24
Well for one thing Apple has done some tricky stuff to prevent movies on their trailer page from being played in anything other than Quicktime.

Only the SD trailers on their page will play for me. The HD links are html redirects or something which throws off Totem.

---

### Post by mc4man on 2010-03-24
They still play fine here using the totem-mozilla plugin though things did run better in firefox several weeks ago. (all inc. HD

chromium browser is working better atm. ( and overall

You need to click on the watch now, then  click on  download, right clicking on  whatever resolution you wish -> open in new tab or open in new window. Then the trailer should play.

Atm here in both firefox and chromium the volume is always reset to zero, so you have to adjust.

Sometimes in firefox the trailer buffers but doesn't start - a pause and restart resolves.

apple trailers now buffer completely while you watch  with totem-mozilla, which  may be very fast depending on your connection speed.

You can also now find them saved in full in /tmp ala youtube.

A possible bug may be they all may not be deleted when you exit the browser. ( only if a reboot doesn't remove

Otherwise a proper mplayer command also works as does a proper wget comm.

screen shows quite a number of trailers in /tmp that haven't been deleted, though probably will upon a reboot - haven't tried.

edit; a mplayer ex. adj cache as needed (copy link from the r. click
```
mplayer -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' http://trailers.apple.com/movies/paramount/ironman2/ironman2-34rgrwt9-tlr2_720p.mov -cache 4096
```

While probably not needed due to caching a wget ex. (uses the same copied link but add the h - shown in red
```
wget -U QuickTime/7.6.2 http://trailers.apple.com/movies/fox/avatar/avatar-tlrf_[COLOR="Red"]h[/COLOR]720p.mov
```

---

### Post by wfp on 2010-03-24
Thanks mc4man for the work around on the apple trailers works for me.

---

### Post by Rob2687 on 2010-03-24
That works with the movies that have those Watch Now style pages but other ones like this [http://trailers.apple.com/trailers/sony_pictures/eatpraylove/](http://trailers.apple.com/trailers/sony_pictures/eatpraylove/) open up in Totem and fail because it's some html page as described previously. 

I've seen a patch a few years ago that works around the redirect thing. I guess it never made it into Ubuntu.

---

### Post by zika on 2010-03-24
I think that I've stumbled, some time ago, on a note that removing **gnome-codec-install** could solve the problem with such pages... I've not tried that yet...

---

### Post by mc4man on 2010-03-24
> That works with the movies that have those Watch Now style pages but other ones like this ...

Those trailers worked fine w/ totem-mozilla till recently - they do play  with the gecko-mediaplayer plugin, either off the r. click in browser window or left click in gnome-mediaplayer.

The copied link can also be played in mplayer and vlc and wget'ed if desired.

(edit; a ways back using the firefox user agent switcher was another option - as to now don't know, don't see the need really

---

