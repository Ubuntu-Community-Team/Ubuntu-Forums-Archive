---
title: "upgrade to 6.10 - blank screen"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by dowbjts on 2007-01-17
I upgraded to 6.10...the splash screen looks fine with progress bar...then when it tries to load the gnome desktop...nothing. Just a blank screen.

I booted up in recovery mode and did the xorg reinstall...when I type xstart from the command line the gnome UI comes up fine.  

What do I need to edit to make it work from a regular boot-up?

HARDWARE:
ATI Rage Mobility driver on LCD screen on Dell L400 laptop

P.S.  Everything worked great with my old Dapper version ](*,)

---

### Post by discord on 2007-01-17
Id try editing your xorg.conf making sure your have the frequency settings  and resolution correct....

---

### Post by dowbjts on 2007-01-17
wouldn't resolution & freq be ok since it works fine when I run startx from a command line?

---

