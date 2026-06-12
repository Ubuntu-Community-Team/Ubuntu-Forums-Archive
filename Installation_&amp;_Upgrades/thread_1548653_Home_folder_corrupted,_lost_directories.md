---
title: "Home folder corrupted, lost directories"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by bigboss0101 on 2010-08-08
Hi all,

In my /home/user folder I only see "Downloads" and "Public" folders. I have lost all the directories like Desktop, Pictures, Videos, Ubuntu One.

And what I see on the desktop is the contents of /home/user. I tried creating Desktop folder in /home/user but that new folder called Desktop itself is being shown on my desktop.

Pls help me restore my Ubuntu. Any help greatly appreciated.

---

### Post by ajgreeny on 2010-08-08
Have a look in gconf-editor ->apps ->nautilus ->preferences and check that there is no checkmark in the desktop_is_home_directory box, as shown in my screenshot.

I can't see why it  would be checked, but it is worth looking.

---

### Post by bigboss0101 on 2010-08-11
No its not checked. Any other ideas please?

---

### Post by bigboss0101 on 2010-08-11
Solved here:
[http://ubuntuforums.org/showthread.php?t=436718](http://ubuntuforums.org/showthread.php?t=436718) (post by wdaniels)

---

