---
title: "keyboard settings"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by oxman on 2012-06-03
I recently did a clean install to 12.04. I'm having a heck of a time with my keyboard settings. The hot keys are no longer the same when using gimp, blender or inkscape. Is there a way to restore my keyboard shortcuts to their classic pre 12.04 settings?

---

### Post by Paddy Landau on 2012-06-03
What do you mean by "hot keys"? Which keys specifically are causing you problems?

A few keystrokes have changed (not many). You can adjust them in System Settings > Keyboard > Shortcuts. However, due to [an existing bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/995885"), you cannot (yet) use the Super key in the shortcuts.

---

### Post by oxman on 2012-06-04
Thank you for your attention.

Well the main culprit is the Ctrl key. In previous ubuntu releases as far back as I can remember, Ctrl worked well in Blender. Using Ctrl+U for instance set my preferences without a hitch. Now I get the same response for Ctrl+U as I do for just plane U and it doesn't set my preferences for the app. 
Another example was the familiar Ctrl+Alt+Backspace for a refresh of the x server. I had to dig into the bowels of keyboard > layout settings >options to gain the standard back. I wouldn't have found it without several queries. 

My hope was that I could simply do a simple adjustment some how and get the old defaults back.

Thanks again!

---

### Post by Paddy Landau on 2012-06-04
Sorry, I don't know Blender. But I have discovered that GIMP (for example) has changed a couple of the keystrokes. That, of course, is nothing to do with Ubuntu or Canonical.

If I knew Blender I might be able to comment. Do you think it may be Blender that has changed the Ctrl-U short-cut?

---

### Post by inashdeen on 2012-06-04
I agree with Paddy. Ubuntu may have change some keystrokes, but app to app changes has nothing to do with ubuntu

---

### Post by oxman on 2012-06-04
According to the blender list of hot keys Ctrl+U is still the norm. I'll do some more homework and ask around the Blender Community. Thanks for your time and effort! It is appreciated.

---

### Post by oxman on 2012-06-05
One of the mouse settings was causing this problem. It turns out that it was an ubuntu setting.

Uncheck "show position of pointer with CTRL key", restart.

---

### Post by Paddy Landau on 2012-06-05
> **oxman said:**
> Uncheck "show position of pointer with CTRL key", restart.
Ah, I've suffered from this before.

You can use Compiz to show your mouse pointer (CompizConfig Settings Manager > Accessibility > Show mouse), but it's rather more fancy than I'd like!

---

### Post by oxman on 2012-06-07
Thanks for your interest.

Life is good again. All of the characteristics of my Crtl function is back to normal. Even my scroll with roll on my mouth works the way it should. I wonder why the change in settings? Do you suppose they are seeking to phase those functions out? I hope not since they are very convenient in my work flow.

---

### Post by Paddy Landau on 2012-06-08
> **oxman said:**
> I wonder why the change in settings?
As far as I can tell, it is an unintentional clash between the features that look for the press of the Ctrl key. As you already found out, turn off the relevant mouse setting and it will work again. If you need the feature, use the Compiz setting as explained in my previous post.

---

### Post by oxman on 2012-06-10
I am very happy with the setup currently. I don't want to have to dig for this again when I do the next LTS version. Not that it in itself is a big issue but death by a thousands cuts is. Perhaps I am thinking too far ahead and stuck in the old gnome desktop mode. I do appreciate your contribution though. thanks!

---

### Post by Paddy Landau on 2012-06-11
> **oxman said:**
> I don't want to have to dig for this again when I do the next LTS version.
It has been accepted as a high-priority bug, so (I hope) you won't have to do it again.

---

### Post by oxman on 2012-06-16
> **Paddy Landau said:**
> It has been accepted as a high-priority bug, so (I hope) you won't have to do it again.

That's what I have always loved about linux-the community. I started in 1997 and haven't looked back. It still isn't smooth sailing but a far cry from Red Hat 5.x :)  Especially for an old goat farmer like me.

---

