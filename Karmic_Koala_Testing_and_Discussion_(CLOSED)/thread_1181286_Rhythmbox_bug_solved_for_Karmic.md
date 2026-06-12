---
title: "Rhythmbox bug solved for Karmic"
date: 2009-06-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thegodsquirrel on 2009-06-07
After recent update Rhythmbox no longer showed an icon in the notification area nor did it give you the ability to hide the whole player to the single Icon in the notification area.

This is solved by going to the edit menu> plugins> check status icon> configure>  Make notifications option: show when the main window is hidden and status icon to: owns the main window.

These settings will restore the function of the icon placed in the notifications and the hidden player.  

Hope this helps someone it took me a minute to figure this out.

---

### Post by pelle.k on 2009-08-23
Hey guys, about that, i'm having this wierd issue with the status icon. When "stopped", it shows a clear crisp icon, but when "playing" it's a downsized, fuzzy icon of the real "playing" icon. Can anyone confirm that?

Also, another issue i'm having, is if i'm listening to the radio plugin (a stream), and stop the player using the status icon, then start the player (again using the status icon), it resumes from my "music library" instead. It would be nice if someone could confirm that too.

---

### Post by Naddiseo on 2009-08-23
> **pelle.k said:**
> Hey guys, about that, i'm having this wierd issue with the status icon. When "stopped", it shows a clear crisp icon, but when "playing" it's a downsized, fuzzy icon of the real "playing" icon. Can anyone confirm that?


I assume that's because I don't have 3d acceleration for my video card. Do you? Want to bug it? and I'll subscribe.

---

### Post by jpeddicord on 2009-08-23
> **pelle.k said:**
> Hey guys, about that, i'm having this wierd issue with the status icon. When "stopped", it shows a clear crisp icon, but when "playing" it's a downsized, fuzzy icon of the real "playing" icon. Can anyone confirm that?
> **Naddiseo said:**
> I assume that's because I don't have 3d acceleration for my video card. Do you? Want to bug it? and I'll subscribe.

That shouldn't have anything to do with it. If anything it's a bug in GTK or more likely Rhythmbox iteslf for failing to set an icon of the proper size (and so GTK scales it down automatically, making it look blurry).

I do notice that the icon width changes when changing play/paused states, so that likely has an effect on the problem depending on what your panel size is set to.

---

### Post by Naddiseo on 2009-08-23
> **jacobmp92 said:**
> That shouldn't have anything to do with it. If anything it's a bug in GTK or more likely Rhythmbox iteslf for failing to set an icon of the proper size (and so GTK scales it down automatically, making it look blurry).

I do notice that the icon width changes when changing play/paused states, so that likely has an effect on the problem depending on what your panel size is set to.

My reasoning was because if you mouseover the indicator it should fade in/out (well it does on my laptop which has 3d acceleration) but on my desktop it should disappears then reappears blurry. And it's not just the icon, but the whole indicator. See attachments.

---

### Post by jpeddicord on 2009-08-23
Hmm... I thought we were talking about the notification **icon** in the panel, not the popups from notify-osd.

> **Naddiseo said:**
> My reasoning was because if you mouseover the indicator it should fade in/out (well it does on my laptop which has 3d acceleration) but on my desktop it should disappears then reappears blurry. And it's not just the icon, but the whole indicator. See attachments.

The blurring is intentional, actually. The notification is supposed to fade and blur out when you move the mouse pointer near it, and re-focus when you move away from it. The next time you see one move your mouse around it and you'll see it.

If the blurry effect sticks even when the pointer is nowhere near the notification, then there's probably a bug in notify-osd.

---

### Post by Naddiseo on 2009-08-23
> **jacobmp92 said:**
> Hmm... I thought we were talking about the notification **icon** in the panel, not the popups from notify-osd.

The blurring is intentional, actually. The notification is supposed to fade and blur out when you move the mouse pointer near it, and re-focus when you move away from it. The next time you see one move your mouse around it and you'll see it.

I've probably misunderstood what the poster before me was referring to. I could have something different: I'm fairly sure mine's video driver related.

It doesn't re-focus for me, once it's blurred it stays blurred. If I keep moving my cursor on and off it changes how blurred it is. I know that if my video card was fully supported, like my laptop, it's supposed to blur in and out like you say.

I'll shut up now. :)

---

### Post by pelle.k on 2009-08-24
Nah, i was referring to the status-icon, in the panel :) Your issue is probably notify-osd related, as jacobmp92 pointed out.

> I do notice that the icon width changes when changing play/paused states, so that likely has an effect on the problem depending on what your panel size is set to.
So that's confirmed then. Great. I'll post a link to the bug report, when i get around to it.

Also, about the other issue, regarding resuming playback (after stopping, obviously) from say a radio source (or maybe a last fm station), could anyone test that?

---

### Post by taavikko on 2009-08-24
> **pelle.k said:**
> 
Also, about the other issue, regarding resuming playback (after stopping, obviously) from say a radio source (or maybe a last fm station), could anyone test that?

It's working correctly here.
but maybe I misunderstood what you need to be tested?

---

### Post by pelle.k on 2009-08-24
> but maybe I misunderstood what you need to be tested? 
You probably got it, since i think i now understand why it didn't work for me. I had items in the "play que", and that apparently has priority over everything else. So i guess it's not a bug, but a feature :) (that is highly subjective, though).
Thanks for the input, made me think twice!

---

