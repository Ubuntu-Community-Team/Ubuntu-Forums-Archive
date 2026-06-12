---
title: "Desktop quirks on upgrade to 10.10"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by pixnaps on 2010-10-10
Just updated from Lucid to Maverick UNE. (It froze at one point, so I killed it from a virtual console and used 'dpkg --configure -a' to complete the installation.)

My question: Isn't the new 'unity' sidebar launcher supposed to replace the old on-screen menu?  We now have both.  And the old menu seems buggy: e.g. the text under some icons is displayed *vertically* (i.e. in a column just one character wide!) instead of horizontally.

Any ideas how to fix this?

---

### Post by pixnaps on 2010-10-10
I should add that the 'locations' option under the clock panel applet seems to be missing.  I can change the date and time, but can't set a location, and so Redshift no longer works.

Also, the Alt-F2 shortcut no longer works.  What's with that?

Update: see attached screenshot, demonstrating the three errors (old desktop menu, vertical icon text, and lack of location option)

---

### Post by kerry_s on 2010-10-10
you have a mix of old & new, in other words a bad upgrade. the new netbook does not have that desktop launcher, just that side bar.

i've already started to tweak mine, but it should be something like this:

---

### Post by pixnaps on 2010-10-11
Thanks, I figured it must be something like that.  Is it possible to fix, or will I need to resort to a clean install?

---

### Post by kerry_s on 2010-10-11
> **pixnaps said:**
> Thanks, I figured it must be something like that.  Is it possible to fix, or will I need to resort to a clean install?

i'd go clean, there's just to many changes & settings.

---

### Post by nkealen on 2010-10-11
> **kerry_s said:**
> you have a mix of old & new, in other words a bad upgrade. the new netbook does not have that desktop launcher, just that side bar.

i've already started to tweak mine, but it should be something like this:
What are some things that you've been able to do and how did you do it? I've been fiddling and searching for a few hours and coming up blank.

---

### Post by kerry_s on 2010-10-11
> **nkealen said:**
> What are some things that you've been able to do and how did you do it? I've been fiddling and searching for a few hours and coming up blank.

not much, what is that you want to do?

---

### Post by nkealen on 2010-10-11
> **kerry_s said:**
> not much, what is that you want to do?
I figured out how to "pin" an app to the sidebar. I'd like to know how to change what folders are the "Favorites"

I use the Ubuntu-one sync folder but have to navigate through so many things to get to it. It'd be great if it was a favorite folder. I don't use video on the netbook, so I'd like to remove that one.  

There are a couple of other things, but they are small issues. I like the interface and I think it's intuitive on the surface, but no simple dragging folders around (even if they still snap-to grid--which is okay) no uses for right-clicking, or even no simple help and configuration is kind of a bummer

---

### Post by pixnaps on 2010-10-11
> **kerry_s said:**
> i'd go clean, there's just to many changes & settings.

Ok, thanks!

---

### Post by paulx1 on 2010-10-13
> **pixnaps said:**
> Just updated from Lucid to Maverick UNE. (It froze at one point, so I killed it from a virtual console and used 'dpkg --configure -a' to complete the installation.)

My question: Isn't the new 'unity' sidebar launcher supposed to replace the old on-screen menu?  We now have both.  And the old menu seems buggy: e.g. the text under some icons is displayed *vertically* (i.e. in a column just one character wide!) instead of horizontally.

Any ideas how to fix this?

I had both menus also after an upgrade. 

However the following seems to have fixed it:

system - preference - startup applications
[INDENT]uncheck - netbook launcher
[/INDENT] reboot.

---

