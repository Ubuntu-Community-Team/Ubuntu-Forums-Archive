---
title: "Skype notifications make totem play."
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gitboxgreg on 2009-10-02
I installed the Karmic beta and I haven't seen any problems except for one. Every time skype shows a notification for when someone goes online of goes offline my paused video in totem starts playing! Has anyone else had this issue?

---

### Post by LKjell on 2009-10-02
> **gitboxgreg said:**
> I installed the Karmic beta and I haven't seen any problems except for one. Every time skype shows a notification for when someone goes online of goes offline my paused video in totem starts playing! Has anyone else had this issue?
EDIT: OBS it is the opposite. BUT still disable it to make sure it is not that module that mess up. Then file a bug report afterwards.

Yeah it is intended [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/437638](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/437638).

I don't quite agree with the one that made the module.

To perm disable, edit the file /etc/pulse/default.pa
and comment **load-module module-cork-music-on-phone**

---

### Post by Longinus00 on 2009-10-02
Comment in that bug report about the regression. It seems they only considered skype pausing playback, not starting it.

---

### Post by gitboxgreg on 2009-10-03
Thanks for the help! I have commented on the bug report.

---

### Post by hugmenot on 2009-10-03
Yeah, this cork plugging thing is implemented by simulating a multimedia button press:

[QUOTE="http://0pointer.de/blog/projects/tagging-audio.html"]For the media players we fake XF86AudioPause key events to make them pause, which probably everyone agress is a terribly kludgy hack.[/QUOTE]

Unfortunately this button /toggles/ play/pause for most players. So, if your player is already paused then it will commence playback. This /is/ a kludgy hack!

Also, when you have one player paused and one other playing it will switch them.

---

### Post by hanzomon4 on 2009-10-03
Ah! So thats what was happening

---

