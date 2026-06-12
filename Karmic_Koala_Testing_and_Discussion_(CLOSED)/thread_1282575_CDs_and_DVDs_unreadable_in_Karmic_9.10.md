---
title: "CDs and DVDs unreadable in Karmic 9.10?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Grimhound on 2009-10-04
I'm using the Karmic beta currently, and I'm having one heck of a time getting any optical media to work. With all the restricted options enabled and all the optional packages in place and installed, still I am unable to play CDs or DVDs. Rhythmbox comes back telling me it cannot identify CDs, while Totem states I do not have the required permissions to play DVDs.

Is there any way to fix it so this functionality works?

Status Update: VLC, as can be expected, once more comes out the gate working near to perfect due to it having everything integrated into itself on installation. However Rhythmbox and Totem refuse to run media regardless of what I do, and I find myself unable to properly rip music from my CDs as well. If anyone has any clues as to fixing them and getting the system to work correctly, please toss them out there.

---

### Post by lancest on 2009-10-04
Did you install libdvdcss2 from [medibuntu]("https://help.ubuntu.com/community/Medibuntu")?  I can play movies on VLC with Karmic 64 and Acid Rip works. (Might stay away from the other players as they are not stable) 
Also sometimes I have to log out/in to get my drive to recognize a DVD. My new Samsung works well- but not perfect.

---

### Post by oboedad55 on 2009-10-04
> **Grimhound said:**
> I'm using the Karmic beta currently, and I'm having one heck of a time getting any optical media to work. With all the restricted options enabled and all the optional packages in place and installed, still I am unable to play CDs or DVDs. Rhythmbox comes back telling me it cannot identify CDs, while Totem states I do not have the required permissions to play DVDs.

Is there any way to fix it so this functionality works?

Status Update: VLC, as can be expected, once more comes out the gate working near to perfect due to it having everything integrated into itself on installation. However Rhythmbox and Totem refuse to run media regardless of what I do, and I find myself unable to properly rip music from my CDs as well. If anyone has any clues as to fixing them and getting the system to work correctly, please toss them out there.

I have all the restricted codecs, etc. installed and audio CDs don't work, They hang Rhythmbox usually. DVDs work, but VLC shuts down after a few minutes.

---

### Post by Squonk07 on 2009-10-04
I haven't tried DVD playback yet, but I've been having similar issues with CD playback.  Would it have something to do with this perhaps:

[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/435035]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/435035")

---

### Post by lxowle on 2009-10-05
I have the same problem - but for me this has something to do with permissions. I can't read the contents of any CD or DVD until I type: sudo nautilus, then suddenly everything appears. Could this the root of your problem also?

---

