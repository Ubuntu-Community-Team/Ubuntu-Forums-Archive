---
title: "Installing Sunbird"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by Aturner on 2007-06-24
Hello, I am running 7.04. I got Sunbird from the package manager, it says it is installed, but I can't seem to find it anywhere! Any clues?
Thanks.

---

### Post by logos34 on 2007-06-24
what about under apps>office?

---

### Post by Aturner on 2007-06-24
Not there

---

### Post by logos34 on 2007-06-24
maybe its not checked.

try:
alacarte

this brings up the menu editor.  Look under office, is it there but box not checked/ticked?  If nothing, you'll have to add a launcher manually.  You installed sunbird deb pkg from repos or downloaded from mozilla?

---

### Post by Aturner on 2007-06-24
It is not there under alacarte. I installed from synaptic package manager

---

### Post by logos34 on 2007-06-24
You could try manually adding a launcher for it:

**sudo gedit /usr/share/applications/Mozilla Sunbird.desktop**

> [Desktop Entry] Name=Mozilla Sunbird Comment=Calendar Settings Exec=**sunbird** Icon= StartupNotify=true Terminal=false Type=Application Categories=Application;Office;

Not sure about the command/executable for it--I compiled mine.  Might be 'mozilla-sunbird' or 'sunbird %u' or something else--look in /usr/bin.

---

