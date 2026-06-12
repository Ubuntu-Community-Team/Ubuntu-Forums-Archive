---
title: "Completely remove and reinstall Firefox"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by annuzzer on 2008-04-20
Due to some compatibility issues (most of the add-ons I work with can't be installed) I removed FF 3B5 and  installed FF2 (via synaptic). Unfortunately not a single one of the formerly installed add-ons worked with version 2 :( . The add-on manager simply tells me that the add-ons will work after a restart (but shows this message even 5 restarts later :( ). So I removed FF with

```
sudo apt-get remove --purge firefox
```

deleted the .mozilla folder within my home folder and afterwards reinstalled FF.

Though I thought I had removed the previous installation completely (including the config-files) the newly FF starts with the formerly used startpage (not the standard one) and lacks some of the icons. After showing the startpage no other URL can be adressed or moved to. Do I get [this thread]("http://ubuntuforums.org/showthread.php?t=210871") right that temporarily removing the gnome-desktop metapackage could be part of a solution?

Thanks in advance...

ann


Edit: Removal and reinstallation of gnome-desktop-data (and depending apps) worked for me.

---

### Post by pfelts on 2008-04-21
I agree that the upgrade to FF3 Beta was a bad move. Bookmarks are lost, saved passwords are lost, add-ons no longer work, JAVA no longer works. :(

---

