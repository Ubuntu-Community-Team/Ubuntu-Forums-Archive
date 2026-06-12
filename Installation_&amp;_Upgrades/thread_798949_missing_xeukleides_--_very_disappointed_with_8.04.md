---
title: "missing xeukleides -- very disappointed with 8.04"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by heindsight on 2008-05-18
about two weeks ago I upgraded my laptop from Ubuntu 7.10 to Ubuntu 8.04, and so far I'm rather disappointed.
My biggest gripe at the moment is that xeukleides has been removed from ubuntu, I use xeukleides quite frequently when preparing figures for documents (I'm doing research in computational geometry). I can't help wondering what other favourite software I'll now have to install from source.

Perhaps it is time I moved on to another distro... :(

---

### Post by HalPomeranz on 2008-05-18
The package name has changed to "eukleides" (no "x" at the front anymore).  So "sudo apt-get install eukleides" should work for you.

Enjoy!

---

### Post by heindsight on 2008-05-18
Yes, I have the eukleides package installed (xeukleides used to depend on eukleides), but it does not include the xeukleides program.

I use eukleides to produce the final figure, but I usually use the interactive features of xeukleides to prepare the figure first -- without it, I'm having to retypeset my tex document every time I make a change to a figure, until I have all my figures exactly the way I want them, rather tedious...

---

### Post by HalPomeranz on 2008-05-18
Huh, this is weird:

```
$ sudo apt-cache show eukleides
[...]
Replaces: xeukleides (<< 0.9.2-1)
[...]
Description: Euclidean geometry drawing language
 Eukleides is a language which allows one to typeset geometric figures
 within a (La)TeX document.  This package includes scripts to convert
 these figures into EPS and other formats.  Eukleides uses a console
 interface.  [B]A separate package, xeukleides, offers a gtk-based
 interface.[/B]
```

Notice the "Replaces:" field seems to contradict the "Description:".  Not sure what's happening here.  You might try emailing the package maintainer(s).

---

