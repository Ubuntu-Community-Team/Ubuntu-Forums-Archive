---
title: "no splash screen - My Wife is going kill me."
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by lakelovers on 2008-05-07
Here's the story: I upgraded to 8.04 from 7.10 on my desktop. Everything went fine except sound which I'm still working on. Then I upgraded my wife's Dell, Insprion 2300 laptop. All went well until the end when the screen went to black. Now, when attempting to log in it doesn't get past the login screen. After giving the user and password, it returns to the login screen (the user and password are correct). After logging in the second time the screen goes redish (pre-splash screen) and the cursor is present and the screen hangs. I've looked at the many posts with the same or similar problems but I got burned out looking for a solution. Can anybody save me? (Actually my wife is very patient)

**Edit:** I went to "options" on the login screen, then to "Gnome Safe Mode" that got me to the splash screen and this error popped up: Problem while loading OAFLLD: Deskbar_applet. and then "Internal error: failed to initialize HAL. I hope this leads to a solution easier.

---

### Post by lakelovers on 2008-05-07
I fixed the problem. Basically, I loggged on in the Gnome safe mode, then went to synaptic, ran updates (a lot of files) twice and reinstalled HAL. On reboot everything worked. . .except the wireless which is a Dell. I've been trying to get "ndiswrapper" to work but without success. "Ndiswrapper" is installed and I've revisited all the posts I receive when I first install "ndiswrapper" but so far it hasn't worked. So, back to researching the problem.

---

