---
title: "emacs extentions doesn't work"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by Agilar on 2011-02-09
Hi

I've just moved from openSuSE to Kubuntu 10.10 - and I find almost all of emacs extentions not working. For example - see the report of
emacs --degug-init

[IMG]http://farm6.static.flickr.com/5016/5430398951_02c602d69a_b.jpg[/IMG]

Here it says that emacs have encoutered problems while loading autopair.el
But it was working on openSuSE! Or I have done smth wrong?

---

### Post by jpkotta on 2011-02-09
Clearly the library isn't there.  You can use the apt-file command to see if a file exists in some Ubuntu package; I checked, it appears that it's not in any packages either.  So for whatever reason, SuSE packages it and Ubuntu (Debian) doesn't.  You you need to find the upstream source (just google for it) and put it where you have your personal .el files (usually ~/.emacs.d/).

---

### Post by Agilar on 2011-03-01
Oh, I solved the problem. The solution is just to set explicitly the path to the extention (before requiring!):

;; autopair
(load "/home/boris/.emacs.d/MyExts/autopair")
(require 'autopair)
(autopair-global-mode 1)
(setq autopair-autowrap t)

---

