---
title: "Cannot watch video (on most players) in Lucid."
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Slorg on 2010-04-18
Hey,

I've got a problem with watching video's in Lucid..
This has been there for a few days and it's still here in a new, fresh install.. (Latest daily built today and all updates)

When I try to watch a video in Totem or in Banshee I get to see the video for +/- half a second, then the screen (the part that should be playing the movie) turns black).
The audio keeps going like it should be and I can see the video again (for half a second, then in turns black again) whenever I change the video size..

Another strange detail is the volume icon in these players, it's back to the old ugly placeholder which was in lucid a few monts ago... (It has this icon in Banshee, Rhythmbox, Totem, actually all players who use the default icon)

I can watch the video's in Rhythmbox and VLC player..
I tried to turn off my compiz effects but nothing helps...

Does anybody know how to fix this and is there anybody else with this issue?

My specs:
Pentium 4 single core 2.6GHz proccesor, 1Gb DDR333MHz Ram, Intel onboard shared memory video card (8mb if I'm not mistaking, does not support pixel shader), 160GB Hard drive from Western Digital, and I think that is all important stuff...

(While I'm at it, I get a 'Ubuntu is checking your drives, this may take a moment, press C to cancel' message when I boot... This only takes less than 4 seconds.. Maybe this is important??)

Thanks in advance ;)

P.S. Here is a screenshot of what happens when I try to watch a video... It's the open video in the examples folder. 
[[IMG]http://img688.imageshack.us/img688/2159/schermafdrukw.th.png[/IMG]](http://img688.imageshack.us/i/schermafdrukw.png/)
You may ignore the red error icon in the corner, Update manager was having an error.. But now I reinstalled my computer so this is not really relevant.

---

### Post by uberlinuxnerd on 2010-04-18
> **Slorg said:**
>  Intel onboard shared memory video card (8mb if I'm not mistaking, does  not support pixel shader) 

I think you answered your own question. What happens if you use a lighter Desktop Environment such as XFCE4?

---

### Post by Khakilang on 2010-04-18
Maybe you can set your on board video RAM to 256MB or 512MB and test it out or the next you might want to check is your VGA driver. To set the video RAM you have to go into the motherboard BIOS setup to set it. That's all I can think of at the moment.

---

### Post by Slorg on 2010-04-18
I don't believe it is my video card...
I've been using Ubuntu since 2006 and it always worked. (I've had this computer since 2008 if I'm not mistaking, always used Ubuntu on this one)
In the whole Lucid release cycle I have never encountered this problem, again I don't think it's the video card..

I also am able to use my desktop effects and run 3d games.. (Not much more than OpenArena and nexuiz, but hey, it works ;))
And again, I can perfectly view my videos (in a really good framerate) with VLC media player...

By the way, I cannot give my video card more memory, my BIOS does not support that ;)

I think it's really strange how my players give me the old volume icon.. Does anyone else has that problem too? (Rhythmbox too gives me the old icon, as seen in the screenshot)

---

### Post by fooman on 2010-04-18
is the ubuntu-restricted-extras package installed?

---

### Post by Slorg on 2010-04-18
Yes it is...
And it actually does not matter that much since this is a completely open video. (The one in the examples folder) ;)
I have this problem with every video by the way.

But everyone has the new volume icon in their players like it should be? :confused:

---

### Post by Slorg on 2010-04-18
Shameless bump...

---

### Post by Uncle Spellbinder on 2010-04-18
> **Slorg said:**
> Intel onboard shared memory video card (8mb if I'm not mistaking, does not support pixel shader)[QUOTE=uberlinuxnerd;9139339]I think you answered your own question. What happens if you use a lighter Desktop Environment such as XFCE4?[/QUOTE]Have you tried that yet?

---

### Post by psyke83 on 2010-04-18
I have the same problem in Totem, but only using XV overlay. Textured XV output doesn't have this problem.

Try opening the video in Totem, and enter fullscreen mode. The video should be visible in fullscreen (if you're having the same problem as I).

---

### Post by psyke83 on 2010-04-18
> **uberlinuxnerd said:**
> I think you answered your own question. What happens if you use a lighter Desktop Environment such as XFCE4?

That's no solution at all.

Slorg,

I think that your graphics adapter has much more than 8mb shared memory - you may be mistaking the 8MB figure (perhaps in your BIOS) as the VGA graphics buffer.

To find the graphics adapter type:
```
$ lspci | grep VGA
```

No motherboard that supports a Pentium 4 class CPU can possibly have such an antiquated IGP that only uses 8MB shared memory.

---

### Post by Slorg on 2010-04-19
> **psyke83 said:**
> That's no solution at all.

Slorg,

I think that your graphics adapter has much more than 8mb shared memory - you may be mistaking the 8MB figure (perhaps in your BIOS) as the VGA graphics buffer.

To find the graphics adapter type:
```
$ lspci | grep VGA
```

No motherboard that supports a Pentium 4 class CPU can possibly have such an antiquated IGP that only uses 8MB shared memory.
I think you are right.
I wasn't sure about the 8mb thing, I just read the number somewhere...
Anyway, the video card is still mediocre but it is good enough to watch video. I don't think it is really the problem.
It is shared memory though..
(Thanks to the terminal command, I found the video card is the following: "Intel Corporation 82865G Integrated Graphics Controller")

I'm still wondering how many megabytes it does have... It's size depends how many RAM it is given. I can't change it in my BIOS so it's kind of hard te see.. My system monitor says I've got 994.1 MiB...


And yes, when I play my video in fullscreen I don't have this problem.. (But only if my desktop effects are turned off)

Running Totem in terminal doesn't give me any errors by the way.
Is there any solution or reason known to this issue.. It's kinda frustrating how I don't even know why this happens :(

---

### Post by warjowuch on 2010-04-19
I think you have got to change your video-output settings. THere are several kinds of videooutput.

Anyone help me out here how to do that?
Linux-Mint has a tool for that by default...

---

### Post by -Robert- on 2010-04-19
> **warjowuch said:**
> I think you have got to change your video-output settings. THere are several kinds of videooutput.

Anyone help me out here how to do that?
Linux-Mint has a tool for that by default...

Totem uses GStreamer. Open a terminal and type: *gstreamer-properties*
You can change the audio and video input/output there, I don't know if it is the solution but it's worth a try.

---

### Post by Slorg on 2010-04-19
It kinda works, thank you,

I chose the video output without xv...
However, I do notice my fps dropped a bit.

It still doesn't fully solve the problem, it looks like it can't handle Xv anymore for some kind of reason. (Honestly, I have no clue what Xv means)

Maybe this has something to do with the Intel video drivers, I had a similar experience before with a similar solution.. (Ubuntu 9.04)
But since it actually didn't solve the thing, the best solution was to install the older Intel drivers. 
The difference this time is that I can watch video's this time, last time the player crashed. Also VLC player works fine, last time it didn't (could be wrong about VLC). Also, this time, my desktop effects work perfectly, last time they didn't.

I do notice a lack of plugins when I open gstreamer-properties.. This is what the terminal gives me:
```
sjoerd@sjoerd-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```
Does that has anything to do with it or should it give these errors?

I'm happy that my video works now, but the performance really decreased :(
In VLC however, I've still got the good old FPS..

---

### Post by -Robert- on 2010-04-19
> **Slorg said:**
> 
I do notice a lack of plugins when I open gstreamer-properties.. This is what the terminal gives me:
```
sjoerd@sjoerd-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```Does that has anything to do with it or should it give these errors?


I get almost the same messages:

```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```I don't know if a missing plug-in could be the cause of your problems? Video playback works just fine here, so I guess most of these unavailable plug-ins aren't really necessary.

---

### Post by seeker5528 on 2010-04-19
> **Slorg said:**
> It still doesn't fully solve the problem, it looks like it can't handle Xv anymore for some kind of reason. (Honestly, I have no clue what Xv means)

If XV output seems totally broken you can add a line in xorg.conf to disable it instead of having to deal with it in each application individually. Assuming you have no xorg.conf the steps would be:

open a terminal window and type:

```
cd /etc/X11
gksudo gedit xorg.conf
```

Then add the lines:

```
Section "Module"
    Disable        "XVideo"
EndSection
```

Save it.

Not totally sure what the situation is relative to restarting X when you log out, but I think it should be enough to log out and log in again.

You can see what modules are loaded by opening a terminal window and typing"

```
xdpyinfo | grep -A 30 extension
```

If that doesn't seem to do it you should be able to log out, it the key combination 'Ctrl'+'Alt'+'F1' to switch to VT1, then type:

```
sudo stop gdm
sudo start gdm
```

After stopping GDM you might have to switch back to VT1 again in order to type the command in to start it again.

Later, Seeker

---

### Post by Reiger on 2010-04-19
None of those `missing' plugins should prevent the app from working. For instance ARTS and ESD are sound backends so totem works with systems that do not use pulseaudio. And the GL looks like it is used for embedding gstreamer (the media library) in OpenGL applications (which Totem isn't one of). 

IOW: Totem (application) != Gstreamer (complex video/sound playback library).

---

### Post by Slorg on 2010-04-25
Ah, it has been solved, it is working now with Xv turned on :) (Thanks to the updates)
Edit: I was wrong, it only works with my desktop effects turned off.. :(

---

### Post by freakyhash on 2010-04-27
> **-Robert- said:**
> Totem uses GStreamer. Open a terminal and type: *gstreamer-properties*
You can change the audio and video input/output there, I don't know if it is the solution but it's worth a try.

:P thanks that helped with the stuttering video..

---

