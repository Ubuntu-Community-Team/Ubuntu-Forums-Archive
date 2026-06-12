---
title: "Can't send pidgin to tray?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ELD on 2009-03-27
How come we can't have pidgin in the tray anymore?

Edit > Nevermind it was just set to never by default, ugh!
Edit2 > realised now you can send it to tray using the notification bit. Weird.

---

### Post by zekopeko on 2009-03-27
> **ELD said:**
> How come we can't have pidgin in the tray anymore?

Edit > Nevermind it was just set to never by default, ugh!
Edit2 > realised now you can send it to tray using the notification bit. Weird.

did you set it or did ubuntu?

---

### Post by ELD on 2009-03-27
This is all from a fresh beta install.

---

### Post by macogw on 2009-03-27
On a fresh install it defaults to "Never" because:
1. The status can be changed with FUSA
2. The hiding can be done with Indicator Applet
3. The notifying of new messages goes to Indicator Applet

So basically it's just a Pidgin-only duplication of platform-wide functionality.

---

### Post by ELD on 2009-03-28
After using it for a while i now realise it, would be nice if the Indicator Applet showed the programs icon by the side of the name instead of just text.

Also the indicator applet's little green circle never seems to grab my attention :(

---

### Post by qweac on 2009-03-28
After a while, Pidgin disappears from my indicator-applet. If I don't have it in the tray when this happens it's completely gone!

---

### Post by zanglang on 2009-03-28
Hmm, it behaves quite inconsistently... (not a fresh Jaunty)

When starting Pidgin with system tray icon set to 'Always', clicking the close application 'X' button minimizes to the tray with its own icon, as expected.

When starting Pidgin with it set to Never (default Jaunty behaviour now?) and closing it almost immediately, Pidgin quits, and the indicator applet icon disappears.

When starting Pidgin with it set to Never, then minimizing Pidgin by selecting it from the applet, and then reopening it, and *then* close the application, it minimizes properly.

Bug?

---

### Post by ELD on 2009-03-28
I would get someone to look into mate.

The close button does seem to send it to the new applet fine for me though (even though pidgin has crashed on me 4 or 5 times today!).

---

### Post by rage-against-windows on 2009-03-28
There was just an update for Pidgin libnotify like 5 minutes ago. Dunno if its a fix or what...

---

### Post by aamukahvi on 2009-03-28
> **rage-against-windows said:**
> There was just an update for Pidgin libnotify like 5 minutes ago. Dunno if its a fix or what...

```
pidgin-libnotify (0.14-1ubuntu7) jaunty; urgency=low

  * /debian/patches/indicate.patch:
    * Making it so that there is also a function watching for
      destroyed conversations and destroying the indicators if
      they're left on the conversations.  This fixes LP: #340717
    * Adjusting the timeout to block new logins when an account
      connects to be 15 seconds.  This helps the flood on slow
      connections.  Also, made it so that logins raise indicators
      that show up in the indicator applet.  Both of these are
      trying to resolve many of the issues in LP: #345494
    * Make it so that icons are scaled to 48x48 at aspect ratio
      so that they don't get squashed.  Patch from Cody Russell
      on LP: #338483

 -- Ted Gould < @ubuntu.com>   Thu, 19 Mar 2009 22:39:59 -0500
```

---

### Post by ELD on 2009-03-29
Has anyone else noticed pidgin seems to just dissapear after a while? Deffinately a bug.

---

