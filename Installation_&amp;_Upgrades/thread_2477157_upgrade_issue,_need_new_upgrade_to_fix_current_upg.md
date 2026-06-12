---
title: "upgrade issue, need new upgrade to fix current upgrade"
date: 2022-07-15
forum: Installation &amp; Upgrades
---

### Post by artunix on 2022-07-15
After the most recent upgrade[ubuntu is always up grading itself] ubuntu is not powering off correctly, because on the next boot up it goes to dev/sda5 and does a file and block clean.

I know it’s not powering off like before because it shows the blinking cursor at the top left of the screen before turning off. Did not do that before. And on power on again the cursor on the upper left then the -cleaning.

Anyone else having this issue ?

ubuntu 20.04.4 lts, 64-bit, gnome 3.36.8, x11




Also different computer same issue with Debian

---

### Post by Impavidus on 2022-07-16
Does it tell you it's cleaning up the filesystem or does it just verify and report that the filesystem is clean? My guess is the latter. It's a common "issue": the splash screen doesn't properly hide all the things that non-technical users don't want to see.

If you want to know the details, you can read the log files, but I don't expect you'll find a real problem.

---

### Post by tea for one on 2022-07-16
While the PC is powering off, press Esc to see messages.
It may give a clue to what is delaying the shutdown.

---

### Post by artunix on 2022-07-16
> **tea for one said:**
> While the PC is powering off, press Esc to see messages.
It may give a clue to what is delaying the shutdown.

there is no delay it just did not show the cursor at the top left of the screen before turning off [before]
press esc while powering off shows/does nothing. I take it from your reply you are not experiencing said issue.

when ubuntu ask about system up grades I always allow it. but I think this last has something wrong with it.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290738&stc=1[/IMG]

---

### Post by tea for one on 2022-07-16
No, I'm not experiencing an unusual shutdown right now.
However, I have witnessed slow shutdowns occasionally where the Esc key has revealed "waiting for snap daemon" or similar.

The message [COLOR="#0000FF"]/dev/sda5: clean[/COLOR] is fine.
I always see the equivalent with my PC when booting.

---

### Post by Impavidus on 2022-07-16
That /dev/sda5: clean message (or something similar) has appeared during startup on my computer for years. Nothing to worry about. It just reports that the filesystem is clean. It is a bug, in the sense that the spash screen should hide the message (unless you disable the splash screen). I'm sure the devs already know about it and consider it low priority. As this anomaly appears not on all computers, it may be a bit hard to track down and with nobody really caring, nothing gets done about it soon.

---

