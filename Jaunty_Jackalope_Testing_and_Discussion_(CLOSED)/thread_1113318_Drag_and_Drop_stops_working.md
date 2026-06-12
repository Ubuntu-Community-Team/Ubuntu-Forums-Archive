---
title: "Drag and Drop stops working"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by scaine on 2009-04-01
This is a weird one, but entirely reproducable.  I'd like someone to confirm, then I'll raise a bug, although I have no idea what would cause this behavour :

Basically, dragging won't work in the lower third of the screen.  You can test by opening two nautilus windows and dragging any file you like to your folder list.  As you do the drag, you'll notice that available "targets" highlight, in order to show that if you dropped there, it would result in an action.  But about two thirds of the way down the screen, these targets stop highlighting and sure enough, if you release at this point, nothing will happen.

You can also replicate this exact behaviour with Thunderbird - open the app and make it very narrow, then position it near the top of your screen - dragging an email to, say, "Junk" will work fine.  Now drag the Thunderbird window to the bottom of the screen and try dragging an e-mail into the junk folder again.  On my system, it refuses to complete the drop action.

Infuriating and baffling.  Please confirm, and I'd appreciate some advice on what I could possibly log this bug against.

---

### Post by macroshaft on 2009-04-01
Not confirmed, seems to work fine here

---

### Post by scaine on 2009-04-01
Thanks there.  This is happening on my Tosh laptop and my Macmini upstairs, both of which were built from a daily image around about Alpha 5.  I think I need a rebuild...  :(

---

### Post by smbm on 2009-04-01
I can confirm this, I've noticed drag and drop has been a bit screwy lately. I couldn't find any specific pattern though, just that it worked sometimes and not others so I didn't report a bug.

---

### Post by scaine on 2009-04-01
Great news - you may have saved me a double rebuild!  Any ideas what might cause drag-and-drop issues in such a wide variety of apps/ways?

---

### Post by smbm on 2009-04-01
> **scaine said:**
> Great news - you may have saved me a double rebuild!  Any ideas what might cause drag-and-drop issues in such a wide variety of apps/ways?

Sadly not unfortunately.

I've only noticed it in Nautilus so far as I don't tend to bother with drag and drop most of the time. I'll have a scout around though.

You could rebuild one machine and see if that fixes it maybe.

---

### Post by smbm on 2009-04-11
I think I might have found something to do with this, I was running as a new user yesterday just to see what Jaunty will look like OOTB and I noticed that drag and drop was working normally.

One of the things have running when logged in as me and not as a new user is Gnome-do/Docky so I tried shutting it down in my main user account and drag and drop functionality was restored. When I started it again it returned to only being usable on the top two thirds or so of the screen.

Can anyone else confirm?

---

### Post by smbm on 2009-04-11
There's:

[https://bugs.launchpad.net/do/+bug/318471](https://bugs.launchpad.net/do/+bug/318471)

It says the fix should be in the next version.

---

