---
title: "Uninstall Software"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by LinuxGenie on 2012-04-19
I just downloaded Nixnote (or nevernote) from a website and it will not open so I want to uninstall it so I can reinstall it. I go to the Ubuntu Software Center and when I got to history and then to the installations tab and I see a whole bunch of names (such as:libtak1.0-0, 2.4.0-0ubuntu1,automatic,libpcsclite11.7.7-2ubuntu2 etc.). How am I supposed to find the correct software to uninstall? I just did an update today and I don't want to uninstall anything I upadated... thanks!

---

### Post by critin on 2012-04-19
> **LinuxGenie said:**
> I just downloaded Nixnote (or nevernote) from a website and it will not open so I want to uninstall it so I can reinstall it. I go to the Ubuntu Software Center and when I got to history and then to the installations tab and I see a whole bunch of names (such as:libtak1.0-0, 2.4.0-0ubuntu1,automatic,libpcsclite11.7.7-2ubuntu2 etc.). How am I supposed to find the correct software to uninstall? I just did an update today and I don't want to uninstall anything I upadated... thanks!

Did you succeed in installing it?  It is a .deb file, right?  If you right click it and choose to let Software Center install it, you can go to it in SC and choose to REMOVE it from there too.  Just search for Nixnote.  
If it isn't there, how did you install it, if you did?

---

### Post by miltonfriesen on 2013-01-06
I downloaded nixnote 1.4 in a .deb package from the official sourceforge link. I clicked on the download and the software center opened and installed it. Now I want to uninstall nixnotes, but I can't find it in the software center. How do I uninstall it then?

---

### Post by ibjsb4 on 2013-01-06
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get remove nixnotes
```

See if that works for you.

---

### Post by Hakunka-Matata on 2013-01-06
You should also be able to see it, and uninstall it via synaptic.

---

