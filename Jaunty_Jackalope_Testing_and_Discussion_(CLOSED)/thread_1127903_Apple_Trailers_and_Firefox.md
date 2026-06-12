---
title: "Apple Trailers and Firefox"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by .Danny on 2009-04-17
What plugins do people use for watching these? So far, whatever I tried ends up either not working or working badly. The plugins that do work give a zoomed in view with a large amount of stuttering making it basically unwatchable.

Also, no matter what I tried I haven't been able to get the "HD" versions watchable at all.

Any solutions for this?

---

### Post by syko21 on 2009-04-17
I use gecko-mediaplayer package along with ubuntu-restricted-extras and w32codecs (or w64codecs for amd64 systems) to play itunes videos. HD and normal ones work without a problem. Tested it just now.

---

### Post by IanW on 2009-04-17
I use [http://www.hd-trailers.net/](http://www.hd-trailers.net/), where I can right-click & save the trailers. VLC will then play them just fine.

---

### Post by SketchyClown on 2009-04-17
> **syko21 said:**
> I use gecko-mediaplayer package along with ubuntu-restricted-extras and w32codecs (or w64codecs for amd64 systems) to play itunes videos. HD and normal ones work without a problem. Tested it just now.

I use the gecko-mediaplayer plugin as well so I'll **X2** this solution.

I use it with the gnome-mplayer package rather than the regular.

Plays flawlessly in Firefox 3.0.8 whereas the mplayer-plugin was crashing the browser.

---

### Post by .Danny on 2009-04-17
> **syko21 said:**
> I use gecko-mediaplayer package along with ubuntu-restricted-extras and w32codecs (or w64codecs for amd64 systems) to play itunes videos. HD and normal ones work without a problem. Tested it just now.

Thank you very much!

I had to remove all the totem and VLC related stuff and then reinstalled mplayer + gecko-mediaplayer and it's now all working.

Cheers.:popcorn:

---

