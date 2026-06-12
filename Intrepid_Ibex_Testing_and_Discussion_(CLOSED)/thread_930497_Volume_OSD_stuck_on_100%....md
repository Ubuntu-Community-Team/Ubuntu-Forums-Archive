---
title: "Volume OSD stuck on 100%..."
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-09-26
...but actually it isn't. Pressing volume up and down keys doesn't change it, nor does the actual volume change. And yet, the volume applet in AWN works correctly. Also, the Volume Control in System>Preferences works fine.

I have had a lot of trouble with media keys on my Dell laptop, and I think maybe this is connected.

---

### Post by rekado on 2008-09-26
Hmm. It's not the same with me on my Haier/Clevo/Uniwill whatever notebook, but there are similarities as the problem is limited to only the hotkeys.

Here's my thread:
[http://ubuntuforums.org/showthread.php?t=926608](http://ubuntuforums.org/showthread.php?t=926608)

and here is the bug I filed:
[https://bugs.launchpad.net/ubuntu/+bug/273009](https://bugs.launchpad.net/ubuntu/+bug/273009)

You could check if you hotkeys produce any key code at all by typing *xev* in a terminal and press the hotkeys. If there is some output this shows that your keys are transmitting but something else doesn't work.

---

### Post by phenest on 2008-09-26
This is a different problem to yours. The volume up/down hotkeys do work, but the OSD permanently shows 100%, and the volume does not change.

In fact, I don't think this is a hotkey problem any more. But a bug never the less.

---

### Post by phenest on 2008-09-26
BTW - This was working fine up to the 25th September.

---

### Post by phenest on 2008-09-29
I have a dual boot with Hardy, and both Hardy and Intrepid share the same /home partition. Now oddly, this same problem is now in Hardy (wasn't before). Is there a config file or something I can change or delete to fix this?

---

### Post by phenest on 2008-09-29
Got it! System>Preferences>Sound - Default Mixer Tracks was set to OSS mixer. I changed it to ALSA and bingo!

---

### Post by rekado on 2008-09-30
Mine always has been on ALSA. Changing it (which I did for several times already) does not fix it unfortunately. So it seems that these two issues are just not related.

---

