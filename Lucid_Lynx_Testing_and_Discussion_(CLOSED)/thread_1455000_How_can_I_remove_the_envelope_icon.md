---
title: "How can I remove the envelope icon"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by The Cog on 2010-04-15
I have an envelope icon in my notification area that I'd like to get rid of (see attached screenshot). I don't use evolution, or chat, and the Set Up Broadcast Account option just gives me a crash report, so I'd like to remove the icon. 

But how? What process is putting it there? I want to keep the notification area because I want the volume control.

---

### Post by philinux on 2010-04-15
I'm guessing you've uninstalled gwibber and evolution?

---

### Post by Elfy on 2010-04-15
remove indicator-messages - just found that out myself.

---

### Post by Atermoon on 2010-04-15
[http://ubuntuforums.org/showthread.php?t=1454025](http://ubuntuforums.org/showthread.php?t=1454025)

---

### Post by 0004tom on 2010-04-15
> **forestpiskie said:**
> remove indicator-messages - just found that out myself.

Yeah but if you do that, then you also lose the icon for Sound, Bluetooth and Rythembox if it's open.

I've tried the Notification Area 2.30.0, which i use for pidgin/xchat and other things, but these things don't show in it anymore.

---

### Post by VMC on 2010-04-15
> **0004tom said:**
> Yeah but if you do that, then you also lose the icon for Sound, Bluetooth and Rythembox if it's open.

I've tried the Notification Area 2.30.0, which i use for pidgin/xchat and other things, but these things don't show in it anymore.

Your right.

What would be even better, is to let the user decide which mail client to put in that envelope. I only use claws-mail.

---

### Post by Elfy on 2010-04-15
> **0004tom said:**
> Yeah but if you do that, then you also lose the icon for Sound, Bluetooth and Rythembox if it's open.

I've tried the Notification Area 2.30.0, which i use for pidgin/xchat and other things, but these things don't show in it anymore.


I removed the indicator applet - then added it again and then it was fine.

I have xchat showing in notification area.

> **VMC said:**
> Your right.

What would be even better, is to let the user decide which mail client to put in that envelope. I only use claws-mail.

Yep - agree with that - seems that we can only have things we want if we agree with whoever's current style over substance thinking is in front.

---

### Post by 0004tom on 2010-04-15
Oh I see what you mean lol

I removed it with apt-get from terminal, logged out and back in, and like magic it was gone.. and the other icons remained

---

### Post by The Cog on 2010-04-15
> **philinux said:**
> I'm guessing you've uninstalled gwibber and evolution?
No. I always leave evolution there, even though I don't use it. I've never seen gwibber - it won't start without crashing. I want to leave it so I can try it if an update fixes the crashes. Neither is runnning a process, so I don't see why they should be responsible for the unwanted envelope.

Removing indicator-messages did the trick. Thanks to everyone for answering.

---

