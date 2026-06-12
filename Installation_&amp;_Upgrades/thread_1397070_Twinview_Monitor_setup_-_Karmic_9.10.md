---
title: "Twinview Monitor setup - Karmic 9.10"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by mylesw on 2010-02-02
Hi there, I'm in the final stages of a total migration from Windows to Linux. I've got a Dell Precision M6300 laptop, with NVidia video capable of Twinhead displays.  On the Windows environment that I was using, I had been using a software product called Maxivista that would allow me to create a virtual desktop spanning a couple of computers.  I had been using this for years, so I'm looking for a setup that mimics what I'm used to.

After a number of hours fiddling around with my settings, I was able to get a Twinview setup running with two 1920x1200 monitors from my laptop - one being driven from the DVI out on it, and the other from the VGA out.  However the way in which it did this wasn't exactly what I wanted.  I'm thinking that what I need to be configured can be done, but it will take me forever to work this out myself, so I'm hoping for some pointers from the community on this.

I'm a software developer by trade so what I need is to be able to have an IDE/Editor on one of my monitors where I can work code, and on the other monitor I need to have a browser where I can test what I do.  Sounds pretty straightforward.  The only problem is that the default Twinview configuration that I'm getting with Ubuntu/NVidia is to have one big desktop that stretches across the two monitors, placing my menu bars across both monitors.  Basically what I need is that monitor 1 is my main screen with its own geometry that all menu bars, toolbars, etc. 'fix' to, but that the 2nd monitor is an extension to that virtual desktop but although setup to be on the 'right of' the primary monitor, it doesn't factor into the overall desktop geometry.  Yet I need it to allow me to drag & drop windows onto it, acts as part of the one computer so I can test within memory on what I'm doing, etc.

Although I'm not an expert in this, what Windows/MaxiVista did was to differentiate between the 'screen' and the 'deskop'.   In other words I could write software that would 'screen center' which would respect the geometry of the screen in which the software was running.  Alternatively I could 'desktop center' which would center across the entire virtual desktop (basically this is not what I want to do).

Can this be setup this way in Ubuntu with a Twinhead monitor configuration?  I just want my screen 0 to be the main screen for everything, where menu bars dock to and don't go beyond, but if I drag the mouse right of that screen it appears on screen 1 and it allows me to drag & drop windows onto screen 1 so I can see them while I'm working on screen 0.  I guess its kinda like the workspace concept of Ubuntu/Gnome, however I want to have workspace 0 on screen 0 and workspace 1 on screen 1.

Can this be done?

Thanks in advance for any pointers.

Myles

---

### Post by audiomick on 2010-02-02
Hi.
I _think_ you want more or less the same as I like to have, i.e. main screen in front of you and a second one where you can "park" things that have to stay open for reference.

The trick with the menu bars (panels) is to right click on an empty part of the panel, select properties (or maybe options. Mine is called "eigenshcaften"), and deselect the option that is called something like "expand". The panel should shrink. Move it to the screen you want, then reselect the expand option. It should then spread to the width of the monitor it is on.

Having done that, I think you will find that things are the way you want. When I move a window from one monitor to the other (yes, it is a twin view setup), I can maximize and have it stay on the monitor it is on. If that isn't working, play around with the desktop effects. I have a vague recollection that this behaviour was different when "no effects" was selected (system> preferences> appearance, fourth tab.)

---

### Post by mylesw on 2010-02-02
Thanks so much for replying to my post.  Yes, you are explaining exactly what I need.  I wasn't aware that by turning off expand on the panels that I could move it to the monitor only that I want (in my case Screen 0).  Thanks for that - I think that will work.

The only question I have is how this can be configured to be setup automatically this way.  I spend about 75% of my time in my office where I have the luxury of 2 x 24" LCD monitors.  I can probably get this working using the information you added and some other stuff I found on the forums here (actually this was really helpful:  [http://ubuntuforums.org/showthread.php?t=859042](http://ubuntuforums.org/showthread.php?t=859042)).

But when I go mobile, and only have my laptop (single 1920x1200 monitor), will I have to manually reset all windows, etc. for this?  Or when I return back to the office after working on the road, will I have to spend a few minutes each time resetting up the displays each time?  Is there a way to have this automated somehow?

Myles

P.S.  Just noticed your an Ozzie in Germany.  I'm an Ozzie in Arizona.  Go figure!

---

### Post by audiomick on 2010-02-03
> **mylesw said:**
> 
P.S.  Just noticed your an Ozzie in Germany.  I'm an Ozzie in Arizona.  Go figure!:p small world...


I'm afraid I can't help with the issue about what happens when you unplug an external monitor when the system is set up for it. The first step would be to try it and see. Before you do that, you might want to make a backup copy of the file /etc/X11/xorg.conf
This file doesn't exist by default on 9.10, but will have been written or written to by the nVidia setup tool. To edit it, you need to start the editor with root privileges, which can be done with
```
gksu gedit
```

I would save it somewhere as a backup before trying anything unknown. If things go pear shaped, you can copy the back-up back, which should get you back to where you were.

As to the question of whether there are any mechanisms for dealin with "profiles", i.e. one situation with the external monitor, one without, I am afraid you will have to wait for an answer from someone else.

---

### Post by mylesw on 2010-02-03
I managed to get the two monitors working in the way that I described (thanks for your suggestions on that - worked like a charm).

I realized that there is a 'trigger' that determines if this configuration is needed.  When I boot my laptop, it boots by default to its native screen (i.e. single LCD panel).  On the Dell machines, there is a FN->Video key combination that tells the machine to send its video to the external monitor.  I believe its some form of interrupt that Ubuntu somehow reacts to, in which the external screens are used.   Basically when this occurs, its at that time that I want the xorg.conf to switch.  I'm not sure if X Windows is doing this, or where it is happening, but I'll dig through it and try and find what occurs and if I can trap that event, then I may be able to intercept it and tell it to switch the xorg configurations around. 

I did find a script that someone wrote that does this and it works pretty well.  I just need to find a way to fire it off when the video is sent to the external monitors and I'm all set.

Again, thanks for your help on this.  

Myles

---

