---
title: "After upgrade all windows open too large"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by brianw0667 on 2013-04-30
After upgrading to 11.10 all windows (except chromium) started opening full screen with the top of the window (with the close button) not visible. This happens with all terminals, bitpim, firefox, synaptic, etc... Even after using alt and left mouse to drag the window smaller the next time it opens it is too big again.  I have read things about compiz causing this but I don't have it enabled (others on this machine do use it) and I have found no way to fix the issue. I like multi-tasking so don't like windows taking up the entire work space.

Any suggestions?

---

### Post by brianw0667 on 2013-04-30
Forgot to mention I upgraded to 12.04 to see if the issue would go away but it is still here.

---

### Post by ibjsb4 on 2013-04-30
Not using compiz; are you using metacity?  If you are, check this setting in gconf.

[ATTACH=CONFIG]242003[/ATTACH]

---

### Post by brianw0667 on 2013-04-30
I am not sure I explained this very well. I don't really care about the titlebars when a window is full screen my issue is that any window I open is automatically opened full screen now and I can't find how to stop it. After resizing a window to the way I like it if I close the window then open the application again it goes back to full screen.

---

### Post by brianw0667 on 2013-07-07
It took a while but after reading another forum post I found out the problem is a program called maximus which is an Automaximizing window management tool that is automatically installed and set to run at startup.

---

