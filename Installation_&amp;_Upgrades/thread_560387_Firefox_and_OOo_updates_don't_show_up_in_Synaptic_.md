---
title: "Firefox and OOo updates don't show up in Synaptic or Update Manager"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by kstella on 2007-09-26
My windows installation updated my Firefox automatically, but no updates for Firefox appeared in either Synaptic or the Update Manager... I also wanted to update my OpenOffice.org to v2.3, but that didn't show up, either. I've clicked reload, but nothing doing. What do you think might be wrong? I'm concerned that there are other updates I'm missing out on, too.

---

### Post by pay on 2007-09-26
Ubuntu patches firefox themselves so it is slightly different from the official one. This might mean that it doesn't need every update if it already has the fixes.

---

### Post by aJayRoo on 2007-09-26
This is because firefox in Ubuntu is kept up to date by the Ubuntu developers (I think) who will package any important updates. This means they will not appear at the same time as the Windows updates to firefox that are delivered straight from Mozilla. Also I believe that it is the Ubuntu policy (if that is the right word) not to upgrade packages to a new version mid-release. What that means is that there will not be an update in the update manager for OpenOffice 2.3, only security updates for version 2.2. Sorry if that wasn't very clear!

---

### Post by gaussian on 2007-09-26
AFAIK, Ubuntu and most other (big) distributions follow different updated policies. Security and stability updates for applications like OpenOffice and Firefox are back ported (typically really quickly) and released for the current version of the distribution. New version (for most part) are not released before distribution update (which at once updates a whole lot of software versions), with some exceptions to most popular software every once in awhile (Firefox?). But, no you are not missing any crucial updates just because you don't see new version of Firefox the day it is available  for Windows.

If you really need a new version of Firefox or OO, there are third party websites giving you several different approaches to install the latest and greates. In my experience (although I don't use OO heavily) I have found that both are mature enough now that I can wait for the next distribution release. Life is just little simpler when you use the packaged software for your distribution.  

You need to ask yourself if you want the latest and greatest that you need to trade off new functionality in those versions against the hassle of keeping up with software that is not part of the official package infrastructure or has been packages by a third party. The problems can range from none to system breakage (depending on what you are installing, from where and what is your experience level with Linux). In practice having alternative version of Firefox or OpenOffice should not be big deals, I have done it earlier for Firefox (when Firefox was in Alpha and Beta stages) with absolutely no problems (this was in a Mandriva system, but that is almost irrelevant). Currently I have a version of Emacs built from source in all my machines to support anti-aliased fonts, but no other major packages outside official package management system.

Personally I would recommend that if you want to install the new versions get them (as binaries) from the official OO and Mozilla websites and install them in either /usr/local or /opt manually. But that is just my personal preference.

---

### Post by kstella on 2007-09-26
That's interesting, I didn't know all that. :) Thanks, guys!

---

### Post by anjilslaire on 2007-09-26
Thats all good, but I noticed that Firefox upgraded itself from 2.0.0.5 to 2.0.0.6 within Feisty. Is 2.0.0.7 not coming til Gutsy, then?

EDIT:
Just realized 2.0.0.7 was a Windows-based Quicktime vuln fix. In that case, we prolly won't see it on 'buntu...

---

### Post by Gremlinzzz on 2007-09-27
I upgraded firefox and now the update manager works so ill get the next update automatically.

---

