---
title: "no video during xubuntu install on vaio pcv-rx550"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by motoperpetuo on 2007-12-23
i'm trying to install xubuntu 7.10 on an older sony vaio pcv-rx550 with 256mb RAM. both blag linux and windows XP run fine on this machine. when I choose the "install xubuntu" option after booting the xubuntu cd, i get the xubuntu splash screen for a while, then my monitor just seems to switch off. that is, i have nothing at all on the display and the green "on" light on the monitor starts flashing on and off.

the hard disk still seems to be doing something, but the display never comes back. any ideas what i might do? is this a situation where i should be using the "install with driver update CD" option? if so, any pointers on how i would get the proper driver and use it?

also, note that i get the same result with the standard ubuntu install CD.

---

### Post by Craigus on 2007-12-23
[http://ubuntuforums.org/showthread.php?p=1541970]("http://ubuntuforums.org/showthread.php?p=1541970")

Your monitor is unable to handle the default settings.

---

### Post by motoperpetuo on 2007-12-23
i checked out that link, and while i understand what it, and you, are saying, i'm still having no luck. here's what i'm doing:

1) boot xubuntu cd.
2) press esc to go to text mode.
3) enter "live vga=791" or "live vga=769"

the results are the same. i've also tried hitting f6 while still in graphical mode at the boot options screen and manually editing the boot options. no luck with this option either.

does anyone have any idea what i'm doing wrong? this is an old, 15" crt monitor i'm working with. should there be a way to get it to work with xubuntu? 

as an aside, i noticed in the help files that the xubuntu live cd requires at least 368MB ram. i've got 256MB. therefore, i suppose i can't run the live cd, but can i still install to the hd?

---

### Post by nzadLithium on 2007-12-23
if there is a text install option you will be fine. Otherwise you will have to download an xubuntu alternate cd.

---

### Post by motoperpetuo on 2007-12-23
the alternate cd worked like a charm. funny. i thought i'd tried that before. anyway, thanks very much!

---

