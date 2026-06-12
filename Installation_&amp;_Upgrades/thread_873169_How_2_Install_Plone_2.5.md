---
title: "How 2 Install Plone 2.5"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by tiberg on 2008-07-28
Hi

Running several Plone sites on windows and would like to install plone 2.5 on ubuntu desktop 8.04.

Tried to install with adapt_manager and it seems that ubuntu come with python 2.5 and plone runs on python 2.4.

Any tips?

/Sven-Erik Tiberg

---

### Post by Partyboi2 on 2008-07-28
what file did you download? Did you download the [[COLOR=Blue]plone2.5-Unifiedinstaller-r3.tgz [/COLOR]]("http://prdownloads.sourceforge.net/plone/Plone2.5-UnifiedInstaller-r3.tgz?download")or did you download the Plone-2.5.tar.gz file? The plone2.5-Unifiedinstaller-r3.tg builds phyton and zope from source. Also the lastest version is [[COLOR=Blue]3.13[/COLOR]]("http://plone.org/products/plone")

---

### Post by kc600 on 2008-08-16
Plone 3 runs on Zope 2.10, which also uses Python 2.4. So whichever one you pick, you'll have to ```
apt-get install python2.4
```.

If you have to use Plone 2.5, i wrote a how-to about installing Plone on Ubuntu Hardy [here]("http://keeshink.blogspot.com/2008/07/installing-plone-25-on-ubuntu.html").

---

### Post by gdoermann on 2009-02-18
Ok, but I'm having issues with the installer.  I have installed python2.4 however, the default version is 2.5.  When I try and install ZopeSkel through ez_install it says there is a compile error.  

I have PIL, gcc, and element tree installed... My question is, are they the incorrect versions?  Do I need to rollback python to 2.4?  if so, can you do that.  The last time I tried something like that my whole Ubuntu distro died...

---

