---
title: "Dapper upgrade desktop-ubuntu not installed"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by Aglystas on 2006-10-24
Hello everyone, I just recently switched over to Ubuntu from windows and was using breezy 5.10 becuase that was the version  that came with the book.  I ran an update using the update manager to get the new version dapper 6.06.  During the installation some of the packages were never installed and this is causing some issues with the OS.  The packages are...

cupsys
cupsys-driver-gimpprint
ubuntu-desktop
bluez-cups
hplip

Also when I was still using breezy there was an unusual error occuring when I would login, and get a brown screen.  After fooling around in shell mode (ctrl-alt-f1) trying to correct the problem I would switch back to the gui and the desktop would be there.  I was hoping that upgrading would correct this issue, but I may have just caused the other packages to not be installed.  I also tried installing them after dapper was running using both synaptic and the command line and neither worked.  And now when I restart I get an error message about the desktop not working correctly.

---

### Post by bulldog on 2006-10-24
Did you try ```
sudo aptitude dist-upgrade
```

Maybe it works,maybe not,give it a try though

---

