---
title: "Can't Boot to GUI After Update"
date: 2013-12-18
forum: Installation &amp; Upgrades
---

### Post by mhrackham on 2013-12-18
I installed some updates today (18 Dec) and afterward I tried to start wow using wine and got a blank screen with the game cursor.  I thought this was odd but decided a reboot would probably clear things up.  Rather, things quickly went from bad to worse.  The system won't boot now.  It varies in exactly what I see on the screen but it will usually get to the ubuntu loading bar screen then cut to a lonely blinking cursor on a blank screen.  At this point I can't type anything but I can access the virtual terminals and my wireless network connection is clearly working because I can use lynx to connect to google.  Trying to startx from the terminal results in a screen of text, most of which flows by too quickly for me to read, but which contains a reference to an api mismatch.

Can anyone tell me what I should do here, or what information I need to retrieve to figure out what's wrong?

---

### Post by Mark Phelps on 2013-12-19
Did you have proprietary video drivers installed? IF you did, those are kernel-version specific and any update that includes a kernel update will "break" those drivers.  If you install such drivers using Additional Drivers, they are then installed in a way that they get updated along with kernel updates.  IF you installed them yourself by downloading a file from a video driver site, you will have to remove those drivers, and then reinstall them.

---

