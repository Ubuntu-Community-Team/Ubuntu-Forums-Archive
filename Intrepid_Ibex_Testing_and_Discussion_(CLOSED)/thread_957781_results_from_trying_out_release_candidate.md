---
title: "results from trying out release candidate"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bartje on 2008-10-24
Hi all,

my experience with Intrepid so far :

1. Firefox tabs extremely slower, sometimes I have to wait a minute before firefox responds again after loading, especially when using my gmail.

*2. clicking : Location => Personal directory (in dutch it's Persoonlijke map) results in VLC starting to play a video, one in my personal directory when no DVD is loaded (I guess the first one alphabetically), the DVD when there is a DVD.*
**Fixed manually**

3. Opening my DVD-recorder, I have to push the button twice, the first time pushing the button (hardware button, on the DVD-recorder itself) results in opening and closing again.

3. Open Movie Editor does not work anymore : 
*openmovieeditor: error while loading shared libraries: libquicktime.so.0: cannot open shared object file: No such file or directory*

*5.Kommander is moved in the menu, from 'Devellopment' to a new menu called '.hidden', Qcad is moved from 'Graphic' to 'Other*'
**Fixed by latest update, today, 25 oct**

The rest I still have to try out. I hope this will be of help to clean things out.

greets,

Bart

---

### Post by Bartje on 2008-10-25
Firefox slowdown fixed by removing the solution for the flash problems on Firefox in Hardy : 
remove beta flash 10, install flash 9

---

### Post by sdowney717 on 2008-10-25
the tray bug is a major pain.

---

### Post by steveydoteu on 2008-10-25
While using Gnome it has been fine.

---

### Post by saisho on 2008-10-25
> **Bartje said:**
> Hi all,

...
*2. clicking : Location => Personal directory (in dutch it's Persoonlijke map) results in VLC starting to play a video, one in my personal directory when no DVD is loaded (I guess the first one alphabetically), the DVD when there is a DVD.*
**Fixed manually**

...


How did you fix it manually? Happens to me also when opening Places -> Desktop (or any other option).
Thanks.
**UPDATE**: Got it fixed by editing .local/share/applications/mimeapps.list

---

### Post by Kleist on 2008-10-26
The major issue has been that I have a low screen resolution (800x600) and my nvidia driver seems not been working even it's installed.
Hope, you guys solve this soon. 
But other than that it's works fine.

---

### Post by kansasnoob on 2008-10-26
> **sdowney717 said:**
> the tray bug is a major pain.

We've discovered a work-around. Posts #25 and #27 here:

[http://ubuntuforums.org/showthread.php?t=942553&page=3](http://ubuntuforums.org/showthread.php?t=942553&page=3)

---

### Post by Bartje on 2008-10-26
> **saisho said:**
> How did you fix it manually? Happens to me also when opening Places -> Desktop (or any other option).
Thanks.
**UPDATE**: Got it fixed by editing .local/share/applications/mimeapps.list

@Saisho:

I fixed it by going into 'my computer' with Nautilus, then moving to my personal directory and changing the 'open with' option with the menu when you right click on it.

Other problem now. I've been doing some video recording lately and editing has become quite impossible. Continuesly all video apps keep crashing after a while, even when I limit the file size of my captures to 500 MB. It happens in kino, kdenlive, and even avidemux has problems with it.

---

### Post by Bartje on 2008-10-26
Another issue.. gtwitter freezes when posting a new line.

---

### Post by jerrylamos on 2008-10-26
Ubuntu boots to black screen on IBM Thinkpad 31 ever since Aug 13 with most Ubuntu builds including Alpha 4, Alpha 5 updated, Alpha 6, Beta, & Release Candidate.

Workaround is to boot in rescue mode and remove compiz.  Permanently.  See Launchpad bug 259385 finally (!) confirmed.

There are more and more posts with more and more hardware/drivers with the similar problems. 

Jerry

---

### Post by Bartje on 2008-10-26
Recently discovered problem :

Brasero : Dragging files from it's own menu to the window with the files to be burnt on disc does not work. Dragging from nautilus into the 'to burn' window does work. Very strange....

---

### Post by Bartje on 2008-10-29
since today Rhythmbox doesn't work anymore. I can't tell after which update, because I didn't start rhythmbox after each update.

Here's what the terminal displays when I start rhythmbox from the terminal.

WARN  coherence                   okt 29 14:08:51  Coherence UPnP framework version 0.5.6 starting... (coherence/base.py:237)
WARN  webserver                   okt 29 14:08:51  WebServer on port 36486 ready (coherence/base.py:106)

(rhythmbox:9166): Rhythmbox-WARNING **: Could not open device /dev/radio0
WARN  rb_media_renderer           okt 29 14:08:51  __init__ RhythmboxPlayer {'shell': <rb.Shell object at 0x2b96af0 (RBShell at 0x1f16140)>, 'no_thread_needed': True} (coherence/MediaPlayer.py:33)
WARN  rb_media_renderer           okt 29 14:08:51  get_volume 1.0 (coherence/MediaPlayer.py:357)
Unhandled error in Deferred:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 243, in callback
    self._startRunCallbacks(result)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 312, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 328, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/python2.5/site-packages/louie/plugin.py", line 103, in called
    return receiver(*args, **kw)
exceptions.TypeError: detected_media_server() takes exactly 3 non-keyword arguments (2 given)

---

