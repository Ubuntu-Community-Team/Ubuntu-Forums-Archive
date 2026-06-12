---
title: "[SOLVED] Need help uninstalling Picasa (which was installed with Automatix)"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2008-02-02
I installed Google's Picasa a while back with Automatix just to check it out, but then forgot about it.  I recently opened it back up because I'm going to make some Web Galleries.  But it doesn't seem to have the upload feature in the version I have installed (or I'm just not seeing where it is; the Windows version has a plain and clear button next to the others at the bottom).

So I'm wanting to take it off.  The problem is when I use Automatix to try and take it off it just sits there for ever doing nothing.  I ultimately end up doing an xkill to force it to quit after 10 minutes of nothing.  So I guess I need to find a way to manually get rid of it.

The program does not show up in Synaptic, so I can't remove it that way.

What should I do?

---

### Post by oldos2er on 2008-02-02
I see a 'Web Album' button at the bottom of mine (v2.7). Also if I right-click on a pic there's an 'upload to web album' choice.

---

### Post by diablo75 on 2008-02-02
The version Automatix installed is older, and doesn't have a Web Album button.  It's not a big deal, but I'd like to get this old copy off and replace it with the latest version.

---

### Post by erfahren on 2008-02-02
sudo dpkg --purge picasa

sudo dpkg --purge automatix2

---

### Post by diablo75 on 2008-02-02
SOLVED - 

I ran automatix again, and noticed that when you hit the "apply" button to tell it to execute whatever you selected, it brings up a new status windows with the bottom half being a terminal readout, but BEHIND the window there was a separate box that popped up, asking me if I wanted to uninstall picasa and google earth (gives the option via check boxes).  It produced and error message at the end, but the good news is the shortcut is gone from the applications>graphics menu, so now I can do a fresh reinstall with google's deb file I just downloaded.

---

