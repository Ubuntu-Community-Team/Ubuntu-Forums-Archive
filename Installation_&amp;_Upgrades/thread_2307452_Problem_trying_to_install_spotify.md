---
title: "Problem trying to install spotify"
date: 2015-12-25
forum: Installation &amp; Upgrades
---

### Post by PedroPV on 2015-12-25
When trying to install spotify, by mistake I inserted my password in the midle of the instation process in the terminal.
Now, the software centre wont open, and there is a erro message 8translating Portugues to English): 
     
    E: O TIPO '---MY PASSWORD----' IS NO KNOWN IN LINE 1 OF THE LIST OF FONTS/ETC/APT/SOURCES/.LIST.D/SPOTIFY.LIST

I copied what was to be copied to my external disk and tried to re-install ubunto from my cdrom, bu it did not work.
What can I do?
Pedro

---

### Post by howefield on 2015-12-25
If the problem is still spotify..

```
sudo nano /etc/apt/sources.list.d/spotify.list
```

and correct/remove the offending line 1. Ctrl + x to save and exit the file. If you are not sure, then copy/paste the contents of the file back here.

If the problem is installing Ubuntu, you'll need to give more details.

---

