---
title: "Revert to Firefox 1.5???"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by casperlingus on 2006-10-27
I just upgraded to Edgy and firefox is very broken.  I believe the problem has to do with upgrading to Firefox 2.0 with a ton of add-ons and flash player already installed.

I would like to first reinstall Firefox from scratch, with none of the add-ons or flash player.  If that doesn't work (like Flash isn't compatible with FF2.0), then I would like to revert back to 1.5 until that's all worked out.

A simple "sudo apt-get remove firefox" wants to remove a lot of stuff I don't want it to remove... how do I go about doing this?

Other options?

Casper...

---

### Post by AiBo on 2006-11-27
Nothing but problems for me as well.  I am very happy with Edgy overall.  Firefox crashing constantly is getting on my nerves.  I have had to revert to Opera to get anything done.  Searching and reading how to revert myself now ...

---

### Post by aysiu on 2006-11-27
If you want to remove all plugins and add-ons, paste these commands into the terminal: ```
mv ~/.mozilla ~/.mozilla.old
sudo mv /usr/lib/firefox/plugins /usr/lib/firefox/plugins.old
sudo mkdir /usr/lib/firefox/plugins
``` If you want to install 1.5, you can do so following these instructions (just make sure you download 1.5 instead of 2.0):
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

