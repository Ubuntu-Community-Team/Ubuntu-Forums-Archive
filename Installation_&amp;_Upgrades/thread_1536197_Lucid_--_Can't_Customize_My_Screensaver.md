---
title: "Lucid -- Can't Customize My Screensaver"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by Solomoriah on 2010-07-21
In all versions of Ubuntu from Hardy to Karmic, I was able to edit /usr/share/applications/screensavers/personal-slideshow.desktop to change the directory used for the "Pictures folder" screensaver.  My change was simple... I added the --location option to the end of the Exec= line so that, instead of Pictures, it looks in Pictures/Screensaver.  This makes my wife happy.

She's not so happy since I upgraded to Lucid.  I've changed the same file in the same way, but it doesn't work.  I've tried adding a new .desktop file in that folder with the instructions I want (and the Name and Comment field changed) but it never appears in the configuration screen.  Heck, I even REMOVED the personal-slideshow.desktop file ENTIRELY and it STILL appears in the configuration program... and works like it did out of the box, with the folder I don't want being selected.

WHAT is going on here?  How do I change this, and more to the point, why did changing it not work anymore???

---

### Post by Solomoriah on 2010-07-21
Okay, never mind.  I found the answer here:

[http://mickcharlesbeaver.blogspot.com/2010_06_01_archive.html](http://mickcharlesbeaver.blogspot.com/2010_06_01_archive.html)

And I'll paste the relevant bit below, so anyone else who wants to do this will be able to find it.  Note, what's shown below is how Mick Charles Beaver did it to create a personalized screensaver.

```
   1. sudo cp condor_logo.svg /usr/share/pixmaps
   2. cd  /usr/share/applications/screensavers
   3. sudo cp footlogo-floaters.desktop condor-floaters.desktop
   4.

      sudo vim condor-floaters.desktop

      [Desktop Entry]
      Name=Floating Condor Logos
      Comment=Bubbles the Condor logo around the screen
      Exec=/usr/lib/gnome-screensaver/gnome-screensaver/floaters /usr/share/pixmaps/condor_logo.svg
      TryExec=/usr/lib/gnome-screensaver/gnome-screensaver/floaters
      StartupNotify=false
      Terminal=false
      Type=Application
      Categories=GNOME;Screensaver;
      OnlyShowIn=GNOME;


   5. sudo /usr/share/gnome-menus/update-gnome-menus-cache /usr/share/applications > /tmp/desktop.en_US.utf8.cache
   6. diff /usr/share/applications/desktop.en_US.utf8.cache /tmp/desktop.en_US.utf8.cache
   7. Make sure the diff looks like what you expect
   8. sudo cp /tmp/desktop.en_US.utf8.cache /usr/share/applications/desktop.en_US.utf8.cache
```
The main thing is the desktop.en_US.utf8.cache (which might well be named differently if you aren't in the US).  Apparently, it's not enough to edit those files... you have to rebuild the cache.

---

