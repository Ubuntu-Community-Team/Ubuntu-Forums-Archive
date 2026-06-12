---
title: "Error Message Displayed"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by sandeepnaik on 2010-12-11
Hey I just installed Ubuntu 10.10 but while completing installation at the point when we remove installation CD from drive and go to press enter to restart the system, I saw this error:

[2993.693601] end_request: I/O error, dev sr0, sector 537844

like this line there were so many line displayed the I pressed enter the PC got restarted and now Ubuntu running as nothing happened. But I couldn't understand what was that error and how much serious it was.

What was that error?

---

### Post by sandeepnaik on 2010-12-11
What should I do now to overcome that error? Please help.

---

### Post by Rubi1200 on 2010-12-11
> 
[LIST]
[*]**I/O error after CD is ejected at end of install.**  In some cases, ejecting the CD at the end of installation will leave errors on the screen such as: 
[/LIST]

end_request: I/O error, dev sr0, sector 437628these  error messages indicate that the system is still trying to access some  files on the CD, and are harmless except that they obscure the message  asking the user to press Enter to reboot.  You can safely remove the CD  from the tray and press Enter at this point to reboot to your new Ubuntu  system. ([539027]("https://bugs.launchpad.net/bugs/539027")) 

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues)

Nothing to worry about :)

---

