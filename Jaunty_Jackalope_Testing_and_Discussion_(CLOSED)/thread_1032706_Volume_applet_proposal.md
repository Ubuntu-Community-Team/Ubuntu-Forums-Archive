---
title: "Volume applet proposal"
date: 2009-01-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-01-06
Since today gnome-volume-control seems to support per-app volume setting. I came up with this mockup, in which these individual sliders appear in the applet too:

[IMG]http://1.bp.blogspot.com/_49lyUbkK9k8/SWPVCgKlo1I/AAAAAAAAAMc/VIjiTRpSp44/s1600/Pantallazo-1.png[/IMG]

Would you like to see something like that? Should I file a bug or something? What do you think?

---

### Post by | MM | on 2009-01-06
For whatever reason, the image mentioned above was not visible and would not open in my browser.  SO here is the link to the image file:

```
http://1.bp.blogspot.com/_49lyUbkK9k8/SWPVCgKlo1I/AAAAAAAAAMc/VIjiTRpSp44/s1600/Pantallazo-1.png
```

I think you need to cut and paste the link into your browser address bar.  At least i do in Opera.

---

### Post by MadMan2k on 2009-01-06
guess what is currently being implemented, genius? ;)
[http://farm1.static.flickr.com/20/70003494_668cfdc0dd.jpg](http://farm1.static.flickr.com/20/70003494_668cfdc0dd.jpg)

[http://gsmartmix.blogspot.com/](http://gsmartmix.blogspot.com/)

---

### Post by | MM | on 2009-01-06
> **MadMan2k said:**
> guess what is currently being implemented, genius? ;)
[http://farm1.static.flickr.com/20/70003494_668cfdc0dd.jpg](http://farm1.static.flickr.com/20/70003494_668cfdc0dd.jpg)

[http://gsmartmix.blogspot.com/](http://gsmartmix.blogspot.com/)


For real?  Thats a mockup and the blog post is dated 2006!?  To me that doesn't give much hope that any quality code exists.  But i hope I'm wrong, because I would love to see such an applet.

---

### Post by ShirishAg75 on 2009-01-06
> **Bou said:**
> Since today gnome-volume-control seems to support per-app volume setting. I came up with this mockup, in which these individual sliders appear in the applet too:

[IMG]http://1.bp.blogspot.com/_49lyUbkK9k8/SWPVCgKlo1I/AAAAAAAAAMc/VIjiTRpSp44/s1600/Pantallazo-1.png[/IMG]

Would you like to see something like that? Should I file a bug or something? What do you think?

How did you guys come to know that gnome-volume-control supports per-app volume setting?

---

### Post by Bou on 2009-01-07
> **ShirishAg75 said:**
> How did you guys come to know that gnome-volume-control supports per-app volume setting?

Well, if you open gnome-volume-control and go to the "applications" tab you can set individual applications' volume.

---

### Post by ShirishAg75 on 2009-01-07
The applications tab only works if some application is running sound atm otherwise its blank.

---

### Post by Bou on 2009-01-07
> **ShirishAg75 said:**
> The applications tab only works if some application is running sound atm otherwise its blank.

Indeed. But I'm afraid I don't get your point.

---

### Post by ShirishAg75 on 2009-01-07
Forget it. 

Another thing though, I don't seem to find a way to do preferences like I could in the old way with checking and unchecking stuff. For e.g. adding adding bass and treble. 

Attaching a picture of the old way.

---

### Post by plun on 2009-01-07
> **Bou said:**
> Would you like to see something like that? Should I file a bug or something? What do you think?

This one is a hard one...

What is best for a newbie  :confused:

A bunch of volume sliders are maybe confusing.


The application volume sliders tab can be reach with 3 clicks...

The best is to have a option for this....maybe :confused:


For my own needs Bou's suggestion is great !!:D



This is also probably something which best is discussed with Gnomes devs ?

I don't believe that Ubuntu changes this GUI...

---

### Post by meborc on 2009-01-07
i think the idea is great... there are some programs that play sound way too low... so i must max out my volume... but then again there are some programs that then make too much noise (some IM notifications etc)... setting volume for different programs (that are running) on the fly would be great **_for me!_**

---

### Post by Gina on 2009-01-07
I've found the volume varies between apps to and, yes, it's annoying.  So I agree it's useful to set each individula app relative to the others.  This is in addition to an overall volune control, of course.

As for newbies, as long as the overall volume control is clearly visible, the individual app controls can be obtained from a menu or whatever.  A win-win situation IMO.

---

### Post by marmuta on 2009-01-07
> **Gina said:**
> I've found the volume varies between apps to and, yes, it's annoying.  So I agree it's useful to set each individula app relative to the others.  This is in addition to an overall volune control, of course.


I agree too, this is good to have and all, but what I really wish for is that all sound has about the same volume without me having to micro-manage individual streams.

I've had hacked something together some time ago that tries to do that in a very crude way with a ladspa plugin. It's far from perfect but I've hardly ever touched volume controls while I used this. No more barely audible or ear-drum smashing youtube videos.
It even had some nice side-effects, like when playing flash-videos, music in the background would go silent and come back again once the video is over.

Unfortunately it broke in Jaunty but I was going to fix it anyway. If there is any interest I would post it.

---

### Post by ShirishAg75 on 2009-01-07
marmuta, put up whatever you have. Who knows somebody might give you something new or may get excited.

---

### Post by MadMan2k on 2009-01-07
> **| MM | said:**
> For real?  Thats a mockup and the blog post is dated 2006!?  To me that doesn't give much hope that any quality code exists.  But i hope I'm wrong, because I would love to see such an applet.
that mockup depended on pulseaudio to be in place, but now that ancient mockup is being implemented...

---

### Post by bash on 2009-01-07
> **MadMan2k said:**
> that mockup depended on pulseaudio to be in place, but now that ancient mockup is being implemented...

Do you have link to some sort of source for this, like a mailing list or a dev blog? I'm curious about this, so I would like to read up more about what the devs have to say about it.

---

### Post by Slug71 on 2009-01-07
> **ShirishAg75 said:**
> Forget it. 

Another thing though, I don't seem to find a way to do preferences like I could in the old way with checking and unchecking stuff. For e.g. adding adding bass and treble. 

Attaching a picture of the old way.

Oh boy, i hope this doesnt mess with my internal microphone.

---

### Post by gnomeuser on 2009-01-07
The new volume applet work is being done by Fedora in GNOME SVN, you can follow the feature here:

[https://fedoraproject.org/wiki/Features/VolumeControl](https://fedoraproject.org/wiki/Features/VolumeControl)

Using the talk page suggestions can be made for improvements. Bugs are taken via upstream GNOME bugzilla.

---

### Post by MadMan2k on 2009-01-07
> **bash said:**
> Do you have link to some sort of source for this, like a mailing list or a dev blog? I'm curious about this, so I would like to read up more about what the devs have to say about it.
the link to the dev blog is in my first post. baiscally you want search about GSmartMix and Pulseaudio.

---

