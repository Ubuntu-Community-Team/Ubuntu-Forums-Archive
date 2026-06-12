---
title: "menu.lst that is not screwed by kernel upgrade"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by vexorian on 2007-06-17
How can I ensure that not to ever happen, today I finally gave upgrade manager a chance to download all those 80MB worth of stuff but huh, I forgot to verify if it was downloading a new kernel so I couldn't see it coming, before this feisty installation the upgrade manager always did very mean things to my menu.lst like making my boot screen back to the black menu and eating my splash screen configuration, so I got used to always backup menu.lst before kernel upgrades but this time I couldn't see it coming...

..To my surprise it kept my splash screen, a little problem was that it removed the windows XP boot entry...  And that's not exactly a good thing if you got family that also use the computer and won't use Ubuntu... So I had to recover the entry manually which takes time...

How can I set menu.lst correctly so upgrade process can recognize my entries?

---

### Post by merlinus on 2007-06-17
Did you move the XP entry to a different location in /boot/grub/menu.lst?

If it does not appear after this line:

### END DEBIAN AUTOMAGIC KERNELS LIST

It will always be deleted upon a kernel upgrade.

A better way is to change the default to whatever the stanza number of the XP entry is, minus one.  For example, if it is five, then set the default to 4.

Then you can change the timeout to a lower value as well.

-merlin

---

