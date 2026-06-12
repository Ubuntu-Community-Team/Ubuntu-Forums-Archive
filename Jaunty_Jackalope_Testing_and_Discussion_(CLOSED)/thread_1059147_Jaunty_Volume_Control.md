---
title: "Jaunty Volume Control"
date: 2009-02-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lee_connell on 2009-02-03
There use to be an easy way in the forums to get to the next ubuntu release in development and post there, did this get removed or am i missing something?

Anyways, in the latest jaunty releases, the gnome volume applet has changed, it is now horizontal instead of vertical, which I must say I preferred the latter. Also there is a "Volume Control" button, does this really follow gnome HIG, I think it is really out of place.  Another more important issue is when you click on the Volume Control button it does not close the applet, it leaves the applet open and opens volume control requiring you to close out of volume control when you're finished and clicking the applet icon again to close that.

---

### Post by cariboo on 2009-02-03
The place you want is [Jaunty testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=352"). BTW the volume control is back to "normal" after updates this morning.

I've asked the mods to move this to the right place.

Jim

---

### Post by Yellow Pasque on 2009-02-03
Yes, there is still a different forum for the development release (a staff member will probably move your thread there).

> it is now horizontal instead of vertical, which I must say I preferred the latter
Ubuntu hasn't made any changes to the default GNOME 2.25 volume control, so if you feel the design is fundamentally wrong, you might want to comment on GNOME's bugzilla.

---

### Post by Yashiro on 2009-02-03
It was just for testing. I believe it should be back to it's old appearance on release.

---

### Post by bapoumba on 2009-02-03
So moved :)

---

### Post by Yellow Pasque on 2009-02-03
> BTW the volume control is back to "normal" after updates this morning.
:? I applied all available updates and restarted my computer. The volume control still looks and functions as it did before.

---

### Post by chrisccoulson on 2009-02-03
> **Temüjin said:**
> :? I applied all available updates and restarted my computer. The volume control still looks and functions as it did before.

Thats because you are still using the now deprecated mixer_applet. This has been replaced by the new gnome-volume-control-applet, which will display as a status icon in your notification area, and has the vertical volume control

---

### Post by amano on 2009-02-03
Please read this: [http://www.hadess.net/2009/01/nb-it-doesnt-actually-look-like-that.html](http://www.hadess.net/2009/01/nb-it-doesnt-actually-look-like-that.html)

The vertical volume control is an upstream design decision. The horizontal volume control was a take from Ubuntu on their own.

---

### Post by chrisccoulson on 2009-02-03
The horizontal volume control is also an upstream design decision. But, as I pointed out, that is the old mixer applet, which Ubuntu isn't using by default. Ubuntu now uses the gnome-volume-control-applet, which still has the vertical slider.

---

### Post by lee_connell on 2009-02-03
I'm using the latest alpha and ubuntu is using the mixer_applet by default.

I tried running the gnome-volume-control-applet and got this:

$ gnome-volume-control-applet

** (gnome-volume-control-applet:4885): WARNING **: Failed to acquire org.gnome.VolumeControlApplet

** (gnome-volume-control-applet:4885): WARNING **: Could not acquire name on session bus

Looks like its reported here: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/319443](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/319443)

---

### Post by Gina on 2009-02-04
I liked the new horizontal volume control (except the scroll wheel working wrong way) - I found it less obtrusive if I left it open when playing music.  Also, I found it very convenient to have to full voulme control available from a button.  When playing music on my main machine in 8.10 (Intrepid) I find the vertical volume control annoying.

That's my opinion.

---

### Post by lee_connell on 2009-02-04
I wouldn't mind the horizontal as much if they got rid of the big ugly "Volume Control" button and the mute checkbox.  You can already right click the mixer and go to volume control preferences, and you should be able to mute by dragging the slider all the way to the beginning.

---

### Post by biasquez on 2009-02-06
in gnome-session-properties which is startup for volume control? i don't have it on my gnome-session and so i don't have volume icon in my tray. running gnome-volume-control from terminal, i have old alsa mixer and running gnome-volume-control --debug i have this error:  no volume control gstreamer plugins and/or devices found. adding gnome-volume applet, i have horizontal level but old alsa mixer panel...

---

