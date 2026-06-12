---
title: "How to prevent blackout of Firefox address bar."
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2014-09-17
I realize this is a Firefox fix, not really a Lubuntu problem per se; however, it seems to happen, only sometimes, when I install Lubuntu 14.04 (Alternate CD image via Live USB stick) on older computers. 'Don't know why, but the URL address bar in Firefox is blacked out and grayed out as if it's being censored from the user's eyes. It's ugly and simply off-putting, especially to users who've had experience with malware in the past. Therefore, I searched for a way to prevent it and, I found it! Shucks, don't ask me where; I really don't remember.

Anyway, here's the solution:

Open a new tab or window in Firefox and type "about:config" in the address bar, then hit <Enter>. You'll be given a warning by Firefox that your warranty may be voided. What warranty? And so what, I can just reinstall Firefox or choose some other browser instead. So click "O.k." or whatever and the page will be revealed. Find the line beginning with "gfx.xrender.enabled" (typing "gfx.x" should take you right to it.) which ends with "=true". Double-click this line and "true" will change to "false." Then restart Firefox. Ta-dah! Annoying problem solved. 

'Somebody think I should submit this annoying Firefox misconfiguration as a bug report? If so, then to Firefox? Or to Lubuntu team?

Thanks!

---

### Post by vasa1 on 2014-09-17
[https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007510.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007510.html)

---

### Post by mörgæs on 2014-09-18
Are you using Intel 865, 845 or similar graphics? Then another solution is adding an xorg.conf as described in the link in my signature. It might take care of other graphics bugs as well.

Removed 'Lubuntu' from the title as the bug is in other Buntus too.

---

