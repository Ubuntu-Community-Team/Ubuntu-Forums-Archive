---
title: "Upgraded 12.04 to 14.04 and password now not accepted"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by Idiens on 2014-08-14
HI, I suckered into pressing the upgrade button on the update manager (files backed-up though) 12.04 LTS to 14.04.1 LTS. The process ran well, if slowly, and ended with a restart.  After restart, I entered my password, it was rejected. I tried it on the tty too, also failed. I am locked out. Any suggestions welcome.

---

### Post by Vladlenin5000 on 2014-08-14
Your keyboard layout might have been changed and if your password contains special characters that accounts for the issue you're experiencing.
In 14.04 you should find an icon at the top right part near the clock. Check if the selection there matches your keyboard layout and select the proper one if it doesn't. Even if it does match change it to the other one - the default EN - and back to the correct layout again.

---

### Post by Idiens on 2014-08-14
Thanks for the answer. My password should not have that problem and the keyboard seems to be the right one.
There is a difference in response when I put in a false password - I get a warning in red immediately above the password entry line. Whereas, the correct password leads to a black screen with flashing cursor, which then reverts to the login screen. 
Another oddity is that the background is that of Precise P and not of TT, although bottom left 14.04 is given.
However, in frustration, I have reloaded 12.04 - which gives me a new problem (another post).

---

### Post by Vladlenin5000 on 2014-08-14
> **Idiens said:**
> There is a difference in response when I put in a false password - I get a warning in red immediately above the password entry line. Whereas, the correct password leads to a black screen with flashing cursor, which then reverts to the login screen.

So your problem is most likely related to a change of graphics drivers and nothing to do with the password. Your thread's title is quite misleading.

There were a few similar reports about the upgrade in computers with nvidia cards -and- using the proprietary driver. If that was your case you simply open a tty - CTRL+ALT+F1 -, log in and purge the nividia drivers. Then reboot and you should be able to login with the GUI and from there install the proprietary drivers again.

---

### Post by Idiens on 2014-08-14
Even with CTRL-ALT-F1 I got blocked at the password with sudo, the terminal also just returns tot the user name and password request after a correct entry. I agree it might well be a Nastyvideia issue, but I came no further.

---

