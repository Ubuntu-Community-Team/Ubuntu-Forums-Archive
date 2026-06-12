---
title: "Another gnome-terminal profile!"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2010-03-09
Hello, I recently noticed that I have two gnome-terminal profiles - Ambience and Default.

I can't delete Ambience! I don't want it!:p

The reason I can't just ignore it is simple - if you have more than one profile, you can't just click New Terminal Window, you have to navigate a submenu and select a profile to use.

It is counter-productive, and frankly, it irritates me that I can't delete a stupid profile - especially since there is a delete button (which doesn't do anything).

---

### Post by tekstr1der on 2010-03-09
> **cyberkilla said:**
> Hello, I recently noticed that I have two gnome-terminal profiles - Ambience and Default.

I can't delete Ambience! I don't want it!:p

The reason I can't just ignore it is simple - if you have more than one profile, you can't just click New Terminal Window, you have to navigate a submenu and select a profile to use.

It is counter-productive, and frankly, it irritates me that I can't delete a stupid profile - especially since there is a delete button (which doesn't do anything).

I agree with every word of this! Haven't really checked out deleting the ambiance profile, but there must be a way.

---

### Post by forumache on 2010-03-10
> **cyberkilla said:**
> 
The reason I can't just ignore it is simple - if you have more than one profile, you can't just click New Terminal Window, you have to navigate a submenu and select a profile to use.

It is counter-productive, and frankly, it irritates me that I can't delete a stupid profile - especially since there is a delete button (which doesn't do anything).

What's wrong with pressing Alt-T to open a new terminal window? Is it not quicker?

The "stupid" profile cannot be deleted because it is not a user defined profile, it is defined at the system level. Maybe the delete button should be grayed out. If you care so much about it, report it as a bug.

---

### Post by Elfy on 2010-03-10
open a terminal - then Edit Profiles, at the bottom cahnge the profile used when launching a new terminal to default

---

### Post by cyberkilla on 2010-03-10
> **forumache said:**
> What's wrong with pressing Alt-T to open a new terminal window? Is it not quicker?

The "stupid" profile cannot be deleted because it is not a user defined profile, it is defined at the system level. Maybe the delete button should be grayed out. If you care so much about it, report it as a bug.

A system level profile for  gnome-terminal? For what purpose? To change the background colour of it? Superfluous.

ALT + T doesn't open a new terminal at all BTW - it opens the "Terminal" menu item. [COLOR="Silver"]It is CTRL + SHIFT + T for me, somehow.[/COLOR] (Misread - this opens a tab, not a new window)

Why have a system-level, locked profile that is indiscriminate from a normal terminal profile, which is *named after ONE theme* when there are many other combinations? Shouldn't "Default" be the default profile, and if they want to interfere with settings and make it bright purple at install-time, then that's perfectly fine.

It doesn't warrant yet another non-configurable, regressive element to be introduced into Ubuntu.

> **forestpiskie said:**
> open a terminal - then Edit Profiles, at the bottom cahnge the profile used when launching a new terminal to default
Thanks for the response, but it isn't quite the solution - instead of File/Open Terminal, having the extra Ambiance profile makes it a submenu: File/Open Terminal/Ambiance OR Default.

This isn't a huge deal, and I didn't mean to make it sound like one. However, it is very much a pointless usability regression if there are two Profiles by default. Hell, even if Ambiance is the only profile on a fresh installation, the name is bad (too specific) IMHO.

---

### Post by forumache on 2010-03-10
> **cyberkilla said:**
> ALT + T doesn't open a new terminal at all BTW - it opens the "Terminal" menu item. It is CTRL + SHIFT + T for me, somehow.

Ctrl+Shift+T opens a new Tab ;)

For a new window, you can press Alt-T if you have your System|preferences|Keyboard shortcuts|Run a terminal keyboard shortcut for Gnome set to Alt-T (as it is the default). The Gnome shortcut will jump first, so Alt-T will never open the Terminal menu (which might be considered a bug, but I like it).

---

### Post by cyberkilla on 2010-03-10
> **forumache said:**
> Ctrl+Shift+T opens a new Tab ;)

For a new window, you can press Alt-T if you have your System|preferences|Keyboard shortcuts|Run a terminal keyboard shortcut for Gnome set to Alt-T (as it is the default). The Gnome shortcut will jump first, so Alt-T will never open the Terminal menu (which might be considered a bug, but I like it).

Sorry, my fault on this occasion. I misread your message. I have my shortcut set to ALT+F3, but it isn't the same - the working directory is not preserved, you see. The right click context menu still works as normal though.

Don't get me wrong, this issue isn't the end of the world, but it's something I picked up on straight away. It is inconsistent and not worth the issues & confusion it brings with it. They should have one profile, named Default.

If they want it to be bright pink when you first install Lucid Lynx, that's fine. It shouldn't be a separate, "system-level" locked profile. There are too many complications from it.

---

### Post by zika on 2010-03-10
Thank You for this thread. I, finally, realized why my window switching (when Terminal is present) is sluggish. It is, simply put, because Ambient profile pushed itself on gnome-terminal. Once I'm back to Default, everything is as it used to be... Great to have things back as they should be...

---

