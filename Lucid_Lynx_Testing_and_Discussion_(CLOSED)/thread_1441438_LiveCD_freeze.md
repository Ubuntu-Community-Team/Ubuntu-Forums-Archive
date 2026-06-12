---
title: "LiveCD freeze?"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rokumanxes on 2010-03-28
I've been trying to test out the beta, but I'm having no luck.
Put the disc in, boot from it, purple screen, ubuntu logo, dots underneath, lookin' nice... dots do their thing, and eventually...
They stay solid, and...  don't move at all.
WLAN light on my laptop flashes occasionally, stays solid a moment, and is pretty... stuck in this cycle.  I shut it off, boot from the disc again, hit the spacebar this time.

Now the typical Language options, and menu show up.
I select English, hit Install ubuntu, it does the dot thing again, doesn't go anywhere.  I tried the... try ubuntu option, and same scenario.

I'm on an acer 5520 laptop, uh... trying to install 64 bit to give it a go, sync ipod touch, test, etc.

If you need anymore info, let me know, if you've any ideas on how I can get this to work, I'd appreciate it.

I've also checked the disc's integrity, and it says there are no errors.

---

### Post by cariboo on 2010-03-28
Try nomodeset under the F6 menu.

---

### Post by VMC on 2010-03-28
You might have to install a newer driver for whatever video card you have. 

You can remove the "quiet" and see if any messages that come out are of help. Also try adding "nomodeset" to linux boot line.

---

### Post by rokumanxes on 2010-03-28
Hey, thanks.
That appears to have worked.  I got some text about ureadahead, or something, but it seems to have loaded up just fine.  I'm installing now.  Thanks a million.
:)

---

