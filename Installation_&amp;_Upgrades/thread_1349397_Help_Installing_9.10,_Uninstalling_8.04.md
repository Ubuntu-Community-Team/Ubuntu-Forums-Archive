---
title: "Help Installing 9.10, Uninstalling 8.04"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Whippersnapper on 2009-12-08
I have a Ubuntu 8.04 (Hardy Heron) installed on the second partition of my hard drive through wubi (first partition is XP). While loading the demo of Ubuntu 9.10, somehow my original 8.04 installation got corrupted. When selecting Ubuntu through the boot up screen, I’d get a “media not found” message.  I tried to install 9.10 over my original installation (8.04), but was unsuccessful. The installation process notified me to uninstall my earlier version, which the uninstall ubuntu program was unable to do. Also, Windows XP’s remove program didn’t recognize the Ubuntu installation on my D drive ( the second partition). Fortunately, I have backed up my data and am looking to install 9.10. My question is this: can I just reformat the second partition then load Ubuntu 9.10 or is there another method of removing 8.04 before installing 9.10?

---

### Post by MelDJ on 2009-12-08
hi there.

8.04 is installed with wubi. hence, to uninstall, in windows, go to control panel-add/remove programmes and uninstall ubuntu. wubi does not install ubuntu on a partition but inside windows like a program.
after that, try installing 9.10. i advise you to install it on its own partition so that it is independent of windows

---

### Post by Whippersnapper on 2009-12-08
I tried uninstalling through Windows "remove program" applet in control panel, but couldn't find any program related to Ubuntu or Wubi.

Could I reinstall 8.04 using that install disk?

---

### Post by MelDJ on 2009-12-08
try this program: [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe ]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe")
try to uninstall your 8.04 with it. i am puzzled why it is not in add/remove

---

### Post by Whippersnapper on 2009-12-09
I couldn't figure it either,,,no program related to wubi or unbuntu in the add/remove program. I previously ran the Ubuntu uninstall program applet, but it seemed like nothing happened. So, I deleted all the files on that partition, then installed 9.10 and voila!!!!!!everything worked as usual with the new OS! I consider this thread Solved!...thank you

---

