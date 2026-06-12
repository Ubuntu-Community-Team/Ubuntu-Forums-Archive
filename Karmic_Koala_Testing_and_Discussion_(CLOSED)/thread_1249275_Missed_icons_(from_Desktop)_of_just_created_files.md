---
title: "Missed icons (from Desktop) of just created files"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GeorgeVita on 2009-08-25
Hi, after a recent download I did not see the **icon of the downloaded file** appearing on my Desktop. There wasn't also at Places > Desktop-File Browser but appeared after reboot.

Later I tested this and is repeatable:

- boot
- at Desktop press "PrtSc" key, and then Save the screen capture to desktop
- repeat above action (print screen) and attend the icons created
>>> 1st or 2nd or 3rd time the 'new file' icon is not appeared
- right click on Desktop and 'Clean up by Name' the same (NOT appearing)
- check Places > Desktop and IS NOT there
- open a terminal window, 'ls desktop' lists OK all files (and missing)
- close terminal window
- press 'reload' button at Desktop - File browser shows all OK

Searching this forum did not found any similar post.

Is this 'my system's' problem (it is updated) or appears also to your system?

**Thanks** in advance,
George

---

### Post by taavikko on 2009-08-25
Just pressed PrtSc and saved it on Desktop, file emerged.
So working correctly here.

just test it with a new user to see if something has b0rked your ~/.settings

---

### Post by kaitwospirit on 2009-08-25
I can repeat this. I often get this from extracting tarballs and rar files or from downloads automatically saved to my desktop, as well. Going to Places->Desktop and clicking refresh or rebooting are the only ways that I know of to make them appear.

---

### Post by GeorgeVita on 2009-08-25
Thanks **taavikko** and **kaitwospirit**!

As the problem remains to me after a recent update dist-upgrade, I am downloading the latest .iso build to do a clean install and check it again.

G

---

### Post by MacUntu on 2009-08-25
+1. The files are there but the desktop needs a refresh (like F5 or your "Clean up by name") before showing them.

---

### Post by | MM | on 2009-08-25
Yea I've seen this.  Nautilus actually seems rather buggy at the moment.

---

### Post by taavikko on 2009-08-25
> **| MM | said:**
> Yea I've seen this.  Nautilus actually seems rather buggy at the moment.

Noticing this too, upon logout there's running processes, usually nautilus still performing something.

---

### Post by kansasnoob on 2009-08-25
Noticed the same thing here. I'd downloaded 3 .debs (not to install but to help someone on the forums) and only 1 .deb showed up on the Desktop until I rebooted and all three were visible.

Same thing happened again saving screenshots to the Desktop.

---

### Post by GeorgeVita on 2009-08-26
Hi again,
I searched bugs.launchpad.net and did not found similar description so I created: 

[https://bugs.launchpad.net/bugs/419058](https://bugs.launchpad.net/bugs/419058)

If above affects to you:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/419058/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/419058/+affectsmetoo)

Regards,
George

---

