---
title: "Fresh install of 13.04, locks up after login"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by IsmAvatar on 2013-05-17
I just did a completely fresh install of 13.04 64bit (actually did it a second time in case it was just a fluke the first time). Everything went smooth. It boots up to a login screen, so I give my password, and then it takes me to my desktop... and then nothing works.
Unity shows up, but is unresponsive.
The top gray bar appears but contains nothing, not even the gear icon that you use to log out / reboot.
I can move the mouse around, but I can't click on anything.
I can press Ctrl+F# to get to tty#, and from there I can do a terminal login and, say, kill gnome-desktop, which takes me back to the login screen, only to have the exact same problem again if I try to login again. The login screen is otherwise completely functional - I can reboot, shut down, change settings, etc., but the moment I try to login from any user account, it breaks.

For the record:
I've installed Xubuntu 64bit on this computer, and it worked fine. However, I want Ubuntu.

Edit: Just tried a fresh install of Ubuntu 12.10. The first boot worked fine. After installing updates and rebooting, it experienced a very similar problem - on login, unity is broken. I can right click and do, like "Set background" or Ctrl+T to open a terminal, but the windows that open don't have window decorations (like no Close button or menus)

I have noticed something that may or may not be relevant. In both Ubuntu 12.10 and Xubuntu, whenever I log in, I get a Crash Report that says Compiz has crashed. I tried installing the proprietary graphics drivers, but that didn't help.

---

### Post by schraube on 2013-05-18
same here. putting the raw disk in virtualbox works for me. but this isn't a solution :)

---

### Post by IsmAvatar on 2013-05-18
I just realized I installed the wrong proprietary driver so it was still using the open source one. Thought I had nvidia. Turns out its ati. Installed the right driver on 12.10 and now it works so I'd try the same on 13.04 next. Might fix it. Let me know if this works for you.

---

### Post by schraube on 2013-05-18
i have nvidia card. but i didn't installed any driver. only ubuntu standard installation without any modifications.

---

### Post by IsmAvatar on 2013-05-18
Definitely try the proprietary nvidia driver then. Look up command line instructions. To enter them, go to tty1 by pressing Ctrl+alt+1.

---

### Post by schraube on 2013-05-18
didn't worked with the nvidia drivers. got an out of range error. i removed the autologin from lightdm.conf (after removing the nvidia drivers). now i can say it has something to do with the autologin because the login screen is working fine. i tried guest session, this also didn't worked. my whole desktop got horizontal flipped %) and mouse/keyboard got crashed.

---

### Post by IsmAvatar on 2013-05-20
Just returning to confirm that this fixed my problem in 13.04 as well. Actually, after I did this, I experienced a watermark that said "AMD Unsupported Hardware", but a quick google search fixed that no problem.

Everything seems to be running smooth now.

Again, this only applied to ATI. I can't speak for NVidia.

It's a pain in the **** that I had to do command line work just to get my OS working immediate after a fresh install, and all just because the open source driver didn't support my hardware at all while the proprietary driver does fine. Hopefully someday they'll improve upon this.

---

