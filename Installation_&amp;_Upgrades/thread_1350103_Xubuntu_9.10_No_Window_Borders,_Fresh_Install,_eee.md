---
title: "Xubuntu 9.10 No Window Borders, Fresh Install, eeepc 1000H"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by rickpref on 2009-12-09
I did a unetbootin xubuntu usb install on a Asus eeepc 1000H twice, first time with the last Beta and then just a few hours ago with the final release of xubunu 9.10.  Each time on this netbook once the install is complete, and even if I update, whatever program I open has no window borders and it attaches itself to the top left portion of the screen, where it blocks the top toolbar.  Can't seem to find anything in the settings menu to fix this.

I've tried installing xubuntu 9.10 twice with different iso's and usb sticks and have had the same problem both times, is anyone else having this problem and know how to fix the window border problem?

thanks

---

### Post by xsilvergs on 2009-12-11
I've just clean installed Xubuntu 9.10 on an old Laptop and have the same problem.

If some one can help please.

[IMG]http://myweb.tiscali.co.uk/xsilvergs/Screenshot.png[/IMG]

---

### Post by xsilvergs on 2009-12-14
Waisted enough time on this so went back and reinstalled 8.10 from CD:-
All fine.
Upgraded to 9.04 from Update Manager
All fine.
Upgraded to 9.10 from Update Manager
Displays correctly, no hidden Menu Bar.

---

### Post by d_yat on 2009-12-23
Hello. Yea I had the very same problem, Just re-installed xubuntu on my parent's pc (as it was not playing nice). Then this happened.
ANYWAY
So yea, The problem can be solved by opening up the terminal and typing
xfwm4 --replace

and that should fix that problem, even when you logoff/turn off your pc.
HOWEVER, it still seems to be missing on the login box...
Does anyone else have this problem too? login box seems wrong too.

---

