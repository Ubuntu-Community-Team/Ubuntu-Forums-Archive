---
title: "HOWTO: Upgrading Dropbox to latest version"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by dark.dimension on 2013-05-12
G'day,
 
Before I dive into explaining what I am trying to do here, let me assure you that I have read the upgrade instructions available at Dropbox support site ([Dropbox - How do I upgrade to the latest version]("https://www.dropbox.com/help/13/en")). However, it doesn't work. 

At the time of writing this post, the latest version of Dropbox is 2.0.10, although my installation had been stuck at 1.6.18 (which was probably the latest when I first installed it). I have tried stopping the daemon first and then using the provided .deb files to upgrade, but it doesn't change anything. Also, the repository added during the install seems useless for many reasons. First, I couldn't upgrade via apt. Secondly, even on Ubuntu Raring, the repository points to Precise!

Anyway, after searching everywhere and not finding a proper solution, I went on doing a little experiment. I installed a fresh copy of Raring on my laptop and then installed Dropbox, which worked perfectly (though the repo link is still pointing to precise; changing it to raring doesn't do anything despite the link being valid)

So on my desktop I realised I had to force the download of Dropbox binary. Pans out to be very simple.

First, stop the currently running daemon. Simply right click on system tray entry and click on 'Quit Dropbox'
Then, move the ~/.dropbox-dist directory to somewhere else; you can also delete it too if you want.
```
mv ~/.dropbox-dist ~/.dropbox-dist.bak
``` Only move this directory and NOT the ~/.dropbox directory.

Then download the latest .deb from Dropbox website and install it in the usual way. I prefer using gdebi for this. Once the installation is finished, you will notice a system notification to start Dropbox. When you do that, it will download the binaries again, only this time it will be at the latest version.

Seems like the auto upgrade doesn't work for some reasons.
Hopefully this helps someone in a same/similar situation.

Cheers,
Abhi

---

