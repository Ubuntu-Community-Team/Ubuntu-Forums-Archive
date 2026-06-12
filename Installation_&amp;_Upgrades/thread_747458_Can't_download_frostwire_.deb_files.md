---
title: "Can't download frostwire .deb files"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by Creole on 2008-04-06
I get the following error when i try to download frostwire .deb files.

/tmp/frostwire-4.13.5.i586-3.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Where can i change the association end which association should i choose.

---

### Post by leonidas666 on 2008-04-06
> **Creole said:**
> /tmp/frostwire-4.13.5.i586-3.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.
This is the message from your browser, right?
It seems you are trying to open file straight away, instead of first downloading it and the working with it locally. Try right-clicking on the link to the file, and then choose "save as", and in the dialog which opens use "save to disk", and not "open with " (assuming you use firefox).
Then use your file manager to work with the file, e.g. nautilus or konqueror.
The Problem is probably that firefox somehow thinks it know how to handle the file, but then, when it actually tries, some helper application is not installed as expected by firefox.

---

### Post by RamR on 2008-04-08
My problem is that the link I am trying to download is for a torrent and it was working since I installed Ubuntu where the torrent would be opened automatically by Deluge.  Now nothing happens except for that error.

---

### Post by Partyboi2 on 2008-04-08
I just tried to download the deb package from [here]("http://www.frostwire.com/download/?os=ubuntu") and had no problem, what site are you trying to download from?

---

