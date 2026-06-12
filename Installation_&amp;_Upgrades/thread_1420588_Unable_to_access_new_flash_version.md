---
title: "Unable to access new flash version"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by jacobite on 2010-03-03
I'm using version 8.04 and have been prompted to upgrade to the latest version of flash, which I did, but although the new version is installed it's not being used by Firefox. I'm still getting the message to upgrade. The version of flash I have is 9.0 r262. Is this a bug? shouldn't Firefox automatically be using the latest version of flash?

Thanks in advance for any advice.

---

### Post by yogesh.girikumar on 2010-03-04
Hi,

You could try installing an alternate flash player or try reinstalling it:
```
$ sudo apt-get --reinstall flashplugin-nonfree
```

Type the following in the address bar:
```
about:plugins
```
See what version of Shockwave Flash is displayed there. The latest is something like 10.0 r45

This tells you what version of flash firefox thinks it has. ;-)

If that doesn't work try reinstalling firefox. Be sure to take a back up of your '~/.mozilla/firefox' directory just to be safe.

Also be sure to export your bookmarks so as not to loose them.

Let me know if that helps.

---

