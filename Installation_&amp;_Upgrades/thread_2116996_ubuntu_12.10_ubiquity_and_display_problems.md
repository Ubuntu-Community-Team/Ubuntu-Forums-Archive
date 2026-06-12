---
title: "ubuntu 12.10 ubiquity and display problems"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by bgold2005 on 2013-02-17
Hi! Simple statement first:
My ubuntu Secure Remix works great. How may I copy its settings to my "regular" 12.10 so ubiquity menu displays (at all)?
If thus can't be done w/o much pain, how can I cleanly uninstall all other ubuntus and leave my 12.10 remix and win 8 dual boot intact? and best way to delete the remaining ubuntu disk space (move to secured remix)?

Details:
Most of my laptops have died. I transplanted my hard drive from my Compaq CQ-62 to my Toshiba L355D-S7825. I was dual booting Windows 8 and ubuntu
(12.04). I also had a little taskbar app that would reboot from windows right into Linux. I state this because i think it put something into the boot that,by itself or with the secure remix, helped reactivate grub so I now can boot into either (grub appears at bootup).

Anyhow, I upgraded to 12.10. yes it gave me the warning about graphics and a supposed procedure to install (gnome-fallback something). So I admit its my fault (well responsibility anyway). 

So I have no menu in ubiquity. Xubuntu (which I somehow have made a default - wallpaper at least [cloud with sun shining thru] also no menu.
Gnome and Gnome (no effects) works fine. Even KDE plasma works (s-l-o-w).

Yet - my ubiquity menu works fine in the 12.10 secure remix!
I should add - all the misfiring ubuntus show my Compaq CQ-62 as a terminal prompt, while the Secure Remix correctly shows satellite as the prompt.

So - can I attempt to fix what seems to be 'should be fixable'?
I hardly know how to phrase the questions, but -- can I force the ubuntus to re-poll/re-identify the graphice hardware/whole pc?
can I clone the Secure remix to other ubuntus?

else how can i copy/save whatever little I have (eg copy home directory?) to the secured remix, dump the old ubuntus while retaining the secure remix (appears at bottom of grub menu) without killing my windows?

I used to have two windows boot items in grub to Win 7, one to sda1
(clean or new boot) and one to sda2 (for hibernated boot)[I didnt do this deliberately somehow I think the toolbar reboot proggie did this but i also used to have wubi so who knows...)
now i have "windows 8" and "windows 7" which do same functions with windows 8.

64 bit (win 8 is 32 bit), 3 GB Ram, ATI graphics ("sysinfo" only ids "VGA compatible graphics. any better hw id linux proggies out there?!)

Suggestions? Thanks!

-Bob

---

### Post by Mark Phelps on 2013-02-17
Unfortunately, sysinfo seems to be mostly worthless when trying to identify video devices.

You should do "lspci" and look for the line containing "VGA".  That should give you the make and model AMD chipset, though with very recent versions and some Mobile versions, it's not very informative, either.

---

### Post by DWade on 2013-05-03
use CRTR+ALT+T and bring up a terminal and at the :~$  type lspci and enter.  It will then list your system information.

---

