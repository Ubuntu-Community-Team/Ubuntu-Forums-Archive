---
title: "Computer crashed in the middle of OpenOffice installation and now I have a problem"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by Pawbla on 2009-11-19
Well, I'm not sure if this should go here, but I hope so.
Anyways, well... My computer crashed in the middle of OpenOffice.org installation, and I had to reboot. I used the bad button because I couldn't move anything :oops:. Now I want to uninstall and reinstall, but it tells me I have to run "sudo dpkg --configure -a". I do so, and it freezes up again.
What can I do to correct this problem?

---

### Post by wojox on 2009-11-19
Try:

```
sudo apt-get -f install
```

---

### Post by Pawbla on 2009-11-19
Still the same message:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by Pawbla on 2009-11-19
I figured out how to look for this in google (I didn't know exactly what to write in the search) and came across [this post]("http://ubuntuforums.org/showthread.php?t=1150289"). I did something similar to this and solved the problem (:. Thanks anyways!

---

### Post by Pawbla on 2009-11-19
Seems to keep crashing at OpenOffice install, though.

---

### Post by phillw on 2009-11-19
Hi, try this one ...

[http://sayeed-linux.blogspot.com/2009/01/install-openoffice-3-in-ubuntu.html](http://sayeed-linux.blogspot.com/2009/01/install-openoffice-3-in-ubuntu.html)

Regards,

Phill.

---

### Post by Hagar Delest on 2009-11-20
In addition to the installation of the Sun version (note that you can download it from the OOo web site), you can [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) (if there is one that has been created) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by Pawbla on 2009-11-26
I didn't know it had changed versions. Thanks!

---

### Post by Pawbla on 2009-11-27
... still crashes.

---

