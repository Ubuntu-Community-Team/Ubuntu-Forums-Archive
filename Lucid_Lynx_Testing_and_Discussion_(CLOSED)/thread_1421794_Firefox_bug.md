---
title: "Firefox bug?"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Easy Lyle on 2010-03-04
Well, I don't know where the true problem is, but I figured I would throw it out and see if anybody else knows ...  Ubuntu 10.04 with daily updates.

I log in.  Start my internet via cellular usb stick.  Open Firefox, and it pulls my old tabs back up cause of my settings.  I can surf, no biggie, but the instant that I type in a url and hit Enter, it drops completely to the login screen.  After logging back in and everything, I can do everything without a problem all day long.  

I don't know if it's Firefox, or something in the background, but I figure I would toss it out here for somebody to hear about it.  Many thanks to all the developers for all their work.

---

### Post by MandeaSaracu on 2010-03-04
I also have a similar problem, but with the update manager.
I log on, click on update manager, click on check for updates, the password prompt appears and when I hit enter, I'm thrown back to the login screen. Then I can work all day, no problem.

---

### Post by Owen.C93 on 2010-03-04
This is a plymouth bug, hitting enter causes gdm to restart. See[ this bug]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/522692") and highlight it that it effects you too. If you don't ant it then you can uninstall plymouth or try the nouveau drivers.

---

### Post by Easy Lyle on 2010-03-04
Many thanks, I marked it as affecting me.  It's not that big of a deal to me, just trying to pass along the info for those that need to know in the development cycle.

---

