---
title: "Movies look like a negative image"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DoubleCross on 2009-09-17
Whenever I try to play a movie on Karmic the movie looks like I am watching a negative of the film. I have checked my graphics card and it seems to be running fine. Any suggestions?

---

### Post by twisted_steel on 2009-09-17
I think had this problem a while back and can't remember how I fixed it, but I did find a few things that might help you out.  All of the videos I watched had a blue hue.

Taken from mgreen's posts at [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/184440):]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/184440%29:")
```
The problem seems to be related to 'xv' (hardware video scaling). Temporary fix is to use sofware/OpenGL video scaling.
For gstreamer applications (Totem etc):
1) 'gstreamer-properties'
2) Under Video tab, choose Plugin: 'X Window System (No Xv)'
 For mplayer:
1) Pick a video out format that is not 'xv'; preferably 'x11', 'gl' or 'gl2' using 'mplayer -vo <format> somemovie.avi'.
---
Workaround for VLC junkies:
1) Settings/Preferences
2) Toggle "Advanced options" on, if you haven't already. (Checkbox in lower right corner.)
3) Click Video/Output Modules in the tree view to the left.
4) Choose X11 (for example) as 'Video output module'.
5) Click Save
 You may have to restart VLC for Video output module changes to take effect.


```

---

### Post by ranch hand on 2009-09-17
Illegal drugs may improve the way it looks to you too.  Sorry, I lived through the 60s.  I do remember it.

---

### Post by DoubleCross on 2009-09-17
I am still not entirely sure how to do that. I am still fairly new at this.

---

### Post by Simian Man on 2009-09-17
Try the compiz negative plugin.  That should put them back to normal :).

---

### Post by DoubleCross on 2009-09-17
The compiz plugin is enabled and its still doing the negative thing.

---

### Post by mdurham on 2009-09-18
> **ranch hand said:**
> Illegal drugs may improve the way it looks to you too.  Sorry, I lived through the 60s.  I do remember it.
Remember what? :)

---

### Post by twisted_steel on 2009-09-18
> **DoubleCross said:**
> I am still not entirely sure how to do that. I am still fairly new at this.

The first step has you run 'gstreamer-proerties'.  In order to do this, you will need to open up a terminal window.  You can find it under Applications -> Accessories -> Terminal.  Enter the text 'gstreamer-properties' (without quotes) and hit enter.  A window should come up and then you can proceed to the next step.  This assumes you are using Totem, also known as Movie Player.

Let us know if you need any other help with the instructions.

---

### Post by Eric Warren on 2009-09-18
[U][I][B]It shouldn't be you're graphic's card try using a different movie player.
the ubuntu 9.04 is a good default for watching video's it come's with one on it.
it's good if you have ubuntu 8.04 or under u can just update it to 9.04 with all you're stuff
im newbie too ubuntu but im just trying to help.

:guitar:
[/B][/I][/U]

---

### Post by Eric Warren on 2009-09-18
oh and also 3djake would know much more then me or if you want to ask me for more help i can get good expert's into it.

---

### Post by Dawnrazor on 2009-09-23
Hello I have got the same Problem

look at this Picture in Attachment

any solutions yet?

---

### Post by LKjell on 2009-09-23
> **Dawnrazor said:**
> Hello I have got the same Problem

look at this Picture in Attachment

any solutions yet?
[http://ubuntuforums.org/showthread.php?t=1273305](http://ubuntuforums.org/showthread.php?t=1273305)

---

### Post by Dawnrazor on 2009-09-24
cool thx :)

---

