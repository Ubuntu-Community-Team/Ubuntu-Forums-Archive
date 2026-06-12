---
title: "nautilus broken with latest update"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by wookiehangover on 2009-04-03
I've been testing Jaunty for a few weeks now, and with the latest update today my system has been practically crippled.

Nautilus refuses to launch, gnome-panel breaks on startup (works if you kill -9 the process), no icons on desktop, generally slow all around. 

I remember seeing some of the Nautilus libs in the last update I ran. Anyone else having trouble?

---

### Post by jocheem67 on 2009-04-03
Hmmmmm, no not really. I did have some problems with gnome-panel, but a simple "killall gnome-panel" did reset the whole thingie.

Did you already turn off compiz?

---

### Post by wookiehangover on 2009-04-03
no, I left compiz on, killed the panel and nautilus and everything is back to (somewhat) normal. Would have been kinda effed tho if I didn't know my way around a shell.

Another update is running now, looks like there are some more gnome fixes in it--I'm pretty confident that this will resolve it's self.

---

### Post by jmmL on 2009-04-03
I think I might be experiencing the same problem. Nautilus locked up after latest round of updates, which I'm pretty sure included some nautilus ones. It refuses to open via gnome-panel or the terminal, and the icons on the desktop are also unresponsive. 

Using top I can see that it is currently using 100% of one of my cores. I can kill it, but it still doesn't return to normal behaviour after that.

Can anyone else confirm?

EDIT: After about a minute in the terminal, the process finally times-out with this error:```

(nautilus:4160): Unique-DBus-WARNING **: Error while sending message: Did not receive
a reply. Possible causes include: the remote application did not send a reply,
the message bus security policy blocked the reply, the reply timeout expired,
or the network connection was broken.
```

---

### Post by wookiehangover on 2009-04-03
are you killing nautilus before you try re-launching it with the terminal?

I took a look through my processes after my last reboot and saw that nautilus was being started with 
```
--no desktop
```

Killing nautilus, then relaunching with alt-F2 (terminal works too, but needs to be kept open = annoying) has been making my system more stable. 

Definitely nervous to reboot again after most current round of updates though. Blerg.

---

### Post by jmmL on 2009-04-04
I think I might have figured it out. If I remember correctly, the first lock-up happened shortly after I resized an icon for a HD video I had on my desktop. I deleted this file using the terminal, rebooted, and everything so far appears to be back to normal.

I was using the terminal to start nautilus, but alt+f2 would have been a better idea, thanks for the reminder.

---

### Post by Bert Mariën on 2009-04-05
Here Nautilus crashes frequently.
I do not know what's going on.
Even the crash report was corrupted.

---

### Post by jerrylamos on 2009-04-05
> **Bert Mariën said:**
> Here Nautilus crashes frequently.
I do not know what's going on.
Even the crash report was corrupted.

Me too.  Is there a launchpad bug?  Any idea what the exact codes are to stop and start nautilus?

Thanks, Jerry

---

### Post by Bert Mariën on 2009-04-05
> **jerrylamos said:**
> Me too.  Is there a launchpad bug?  Any idea what the exact codes are to stop and start nautilus?


I do not know about a Launchpad report yet. The last time Nautilus crashed here and I wanted to file a bug even the report was corrupted. But I will file the next time Nautilus crashes here. 
If the crash report is usable....

---

