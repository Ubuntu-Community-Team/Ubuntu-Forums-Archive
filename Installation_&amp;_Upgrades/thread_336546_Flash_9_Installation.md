---
title: "Flash 9 Installation"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by teaguepatrick on 2007-01-11
So I'm trying to install Flash 9

First I removed Flash 7

and then I followed the instructions in the .txt file, moving the .so file into my firefox plug-ins folder, but when I do that I'm told that I "don't have permission to write to this file."

What am I doing wrong?

---

### Post by bruenig on 2007-01-11
Open a terminal and do the following

First change into the extracted directory
```
cd /path/to/extracted/flash9/directory
```

Then move over the .so, you need to use sudo because it requires root privileges, that is probably where your error is coming from.
```
sudo mv libflashplayer.so /usr/lib/firefox/plugins/
```

---

