---
title: "Are there plans to integrate Pulseaudio as a default volume control?"
date: 2008-06-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-06-09
When I double-click the volume applet on my panel, I get this:

[IMG]http://img214.imageshack.us/img214/1899/pantallazo1lo3.png[/IMG]

Not very compelling, is it. I would rather see something like pulseaudio's volume control, with a couple tweaks:

[IMG]http://img381.imageshack.us/img381/2557/pantallazowr6.png[/IMG]

Do you know if there are any plans to further integrate pulseaudio, make the apps' volume widgets control their PA sliders, and use it as the default volume control?

EDIT: I just found this [idea]("http://brainstorm.ubuntu.com/idea/7482/") about a pulseaudio applet:

[IMG]http://img261.imageshack.us/img261/7606/pulseaudioqo6.png[/IMG]

That would be seriously cool...

---

### Post by psyke83 on 2008-06-09
That would be pretty awesome, yes :).

By the way, GNOME's Volume Control applet did recieve some love recently, although no PulseAudio integration. Screenshot attached.

---

### Post by hexion on 2008-06-10
I'd love the applet the way Bou **showed** it :)


Another cool feature would be the choice to use the function keys of the keyboard so instead of changing the master volume they just change the focused application's volume.

Or maybe leaving the function keys for the master volume and setting up other shortcuts to change the focused application's volume.

---

### Post by Bou on 2008-06-10
The applet is not my design, actually, it belongs to the guy who wrote the Brainstorm idea.

---

### Post by RAOF on 2008-06-12
The 'volume applet controls application volume' idea is both cool and may well be possible for gstreamer-using apps.  That'll require either changing the 'volume' gstreamer element, or adding a new 'pulsevolume' and making playbin autoplug it.

---

### Post by soccerboy on 2008-06-13
+1.  I have been looking for this feature since Feisty Fawn but I figured that it would trickle in as soon as Pulse Audio was made default.  I got my hopes up when I saw PulseAudio integration in Hardy.  I have been expecting it ever since Vista included it since Ubuntu beats Vista feature-wise in just about every department.

---

