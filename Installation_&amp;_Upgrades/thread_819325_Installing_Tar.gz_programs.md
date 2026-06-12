---
title: "Installing Tar.gz programs"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by Retrospekt on 2008-06-05
I've extracted the folder but I'm stuck there.  I'm trying to install the latest Firefox Beta (3RC2).  I read all the guides but I can't figure it out.  All I have is a folder with a bunch of random files in it.

---

### Post by fsmithred on 2008-06-05
If you extracted it into a folder called 'firefox' in your home directory, then you can start it from a terminal by running 'firefox/firefox' or the full path, '/home/Retrospekt/firefox/firefox'

If it works, you can put that path in the command line of the firefox panel button. (right-click on the button and select Properties.)

No need to do ./configure and make. The firefox tarballs are ready to go.

---

### Post by cdtech on 2008-06-05
Just a site I ran across for installing Firefox Beta:

[[COLOR="DarkRed"]Firefox 3 Beta 2[/COLOR]]("http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html")

Hope this helps.......

---

### Post by fsmithred on 2008-06-05
Oh yeah, good idea to backup your ~/.mozilla folder. I would modify those instructions so as not to overwrite the current firefox. Instead of making the symlink to /usr/bin/firefox and changing the menu, just create a new panel button pointing to the new firefox.

---

