---
title: "Low Volume with new volume control"
date: 2009-01-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dudude on 2009-01-06
I am having an issue with the new gnome volume control applet in that it does not allow me to set the volume as high as with previous versions of Ubuntu.

Before I could set the master volume on the Alsa mixer device as well as the volume on the OSS mixer (SigmaTel STAC9227 in my case). By setting the OSS mixer volume higher, I could get a much louder output.
It seems now that, with the new applet, I can only control the master volume of the Alsa mixer device.

Is there any way to work around this issue for now?

Edit: Attached image showing windows. Top images are working Intrepid install, bottom ones are Jaunty install.

---

### Post by plun on 2009-01-06
I had the same challenge with my USB sound system
[B]
Meny System > Prefs >  Sounds[/B] and then check what controls the volume   (box at bottom)

Also check output

---

### Post by ShirishAg75 on 2009-01-06
screenshots might be helpful here. Check out the ones I attached to the great fixes thread. It might give some insight.

---

### Post by dudude on 2009-01-06
Everything seems to be the same as my Intrepid install, except that the OSS volume control is now inaccessible (at least conveniently).
If I move the volume slider to the left third the volume is so low that it becomes inaudible.

---

### Post by pferraro on 2009-01-06
Try this:
Right click on your volume applet, and choose Preferences.
Set the device to the Alsa mixer, and make sure that all of the tracks are at full volume (e.g. Master, PCM, etc.).  Now set the device back to the PulseAudio mixer (e.g. Playback: ...).  Your PulseAudio master track should now go to up to full volume.

---

### Post by ShirishAg75 on 2009-01-06
That is a slightly convulsed way of doing the thing. The same thing can be done by going to System > Preferences > Sound. If needed to work through it you can also right-click the icon and put it on desktop and/or panel if you need to work/experiment it for longer time as well.

---

### Post by plun on 2009-01-06
System>prefs>sound is gone after latest updates.....

Compiz also broke...

I now also have 2 volume controls at systray...  (had the same with gnome-media from source)


"transient conditions" :D

---

### Post by dudude on 2009-01-06
Right clicking on the applet and changing the device to control to "Front" and maxing out the volume does help immensely, but it still seems to not be as loud as it was in Intrepid by maxing out master and front under the Alsa mixer while at the same time maxing out the volume with the OSS mixer.

---

### Post by plun on 2009-01-06
Also check this from the terminal

```
alsamixer -Dhw
```


compared with a plain

```
alsamixer
```


-----------------------------

Sound-prefs is gone....

> gnome-control-center (1:2.25.3-0ubuntu1) jaunty; urgency=low

  * New upstream release
   General:
    - **Remove sound capplet and documentation, it moved to gnome-media**


---

### Post by cszikszoy on 2009-01-06
try running the following in a shell and make sure that all the sliders are turned all the way up.
```

$ alsamixer -D hw:0

```

---

### Post by dudude on 2009-01-06
Here is a screen shot of the alsamixer -Dhw command (the alsamixer -D hw:0 command gives the exact same output)

The only thing that cannot be seen in the screenshot is the "Swap Center/LFE" which is set to off.

"alsamixer" without any arguments shows the pulseaudio device with the only thing being configurable is the master channel.

---

### Post by plun on 2009-01-06
I have no more clues and a bug report for this is probably needed

Must be against gnome-media

[https://launchpad.net/ubuntu/+source/gnome-media/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/ubuntu/+source/gnome-media/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

-

---

### Post by John Jason Jordan on 2009-01-14
> **cszikszoy said:**
> try running the following in a shell and make sure that all the sliders are turned all the way up.
```

$ alsamixer -D hw:0

```

Thanks, that solved the problem for me. Previously I had used just "alsamixer" and all it showed was "master" and "PCM," both of which were at the max. Using the -D hw:0 option I was able to see all the sliders. Once I got them all turned up the volume was back to normal.

Someone should still file a bug report or something. The audio volume was fine before installing pulseaudio. Installing pulseaudio should not have changed the previous settings. Or if it can't be helped that it must change the previous settings, then at least the means to set it right should be plainly visible to users. I should not have had to spend a full day googling and searching the forums for this solution.

Edit: Oops, didn't realize this thread was for Jaunty, My problem was on Intrepid x86_64.

---

