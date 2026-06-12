---
title: "Deleting bottom panel and wma codecs"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bri5569 on 2010-03-28
I have searched quite a few threads regarding the above. 10.04beta is working brilliantly on my Dell Mini 10v but as it is a netbook I would like to remove the bottom panel and have all open windows minimize to the top panel - how do I achieve this (I know how to add things to the panel but which one makes open windows show on the panel) 
Secondly Dell shipped my netbook with its own version of 8.04 but it does include all the necessary codecs to play all variety of files. To date I can not play wma files in Rythmmbox. in 10.04. What do I need to download to achievde this? Have only got used to Ubuntu so please go easy with me in your replies.

---

### Post by mc4man on 2010-03-28
> To date I can not play wma files in Rythmmbox

You should be able to play most wma files in 10.04 (rhythmbox or whatever

Those would include wmas(voice), wma2, wma3 (pro, 9.1,10

You can not atm play wmal (lossless) in gstreamer, though on a 32 bit install installing w32codecs and player that uses them will work. (mplayer, most xine based players.

To enable ryhthmbox to the extent it can be, run this in a terminal (Applications -> Accessories -> Terminal, copy and paste the below in, press enter

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

(if you have wmal, post back

---

### Post by bri5569 on 2010-03-28
Thanks - thats one problem solved - any idea on the panel?

---

### Post by mc4man on 2010-03-28
> I know how to add things to the panel but which one makes open windows show on the panel) 
That would be typically be the 'window list' applet, which adds from left to right so add it to the top panel just to the right of firefox or the ? icon.

Then delete your bottom panel

---

### Post by mikio on 2010-03-28
may i suggest the following solution that works well on my small resolution screen:

enable the autohide property of the panels. then open gconf-editor and set these properties:

/apps/panel/default_setup/toplevels/bottom_panel/auto_hide_size 1
/apps/panel/default_setup/toplevels/bottom_panel/hide_delay 0
/apps/panel/default_setup/toplevels/bottom_panel/unhide_delay 0

i have the same set for the for top_panel. thereby all my windows occupy the whole screen - 2px. and when i need any of the panels they pop out without a delay. works very well for me.

hope this helps

---

### Post by bri5569 on 2010-03-29
(if you have wmal, post back

I must have this as one of my albums will not play - it says I need to install Windows media audio 9 decoder - but when it searches it can not find a plugin.

---

### Post by mc4man on 2010-03-29
Hopefully that album is wmal and not that you're having an issue with wma3 (or files are drm'ed

If you're on a 32 bit quite easy to deal with, 64 bit not quite so.
(if unsure run this in terminal, Ex. of 32 bit install
> doug@doug-laptop:~$ uname -m
[COLOR="Blue"]i686[/COLOR]

So if on 32 bit to start go here, click on the 'i386' link and gdebi will either offer to install or save, if so let it install - screen, (sometimes it may just save - to downloads, if that occurs then just d. click on the downloaded .deb to install

[http://packages.medibuntu.org/lucid/w32codecs.html](http://packages.medibuntu.org/lucid/w32codecs.html)

for a player either mplayer and a front end such as smplayer or gnome-mplayer or a xine based player like amarok though i can hardly recommend the current amarok 2, *though it will work*  (use the pana fork of amarok 1,4 here

For a simple frontend to mplayer

```
sudo apt-get install mplayer-nogui gnome-mplayer
```

For a more useful frontend
```
sudo apt-get install mplayer-nogui smplayer
```

If desired you can easily use mplayer to to convert the wmal to wav and then anything you wish (flac would be good

If on a 64 bit install then things get a bit more involved though certainly doable

(I hope I'm not taking this too literally, if so mention.

> Have only got used to Ubuntu so please go easy with me in your replies. 


---

### Post by bri5569 on 2010-03-30
mc4man - you are a star. Album now playing - it's the old Bad Animal album by Heart. It's people like you why I have ditched windows for good. Thanks once again for all your help.:KS

---

