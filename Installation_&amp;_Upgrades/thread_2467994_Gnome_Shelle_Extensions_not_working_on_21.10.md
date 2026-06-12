---
title: "Gnome Shelle Extensions not working on 21.10"
date: 2021-10-15
forum: Installation &amp; Upgrades
---

### Post by rudolf-kunzli on 2021-10-15
I upgraded to 21.10
I booted the system with Gnome on Xorg
gnome-shell-extensions is installed
chrome-gnome-shell is installed
I am getting the error
---
Although GNOME Shell integration extension is running, native host connector is not detected. Refer [documentation]("https://wiki.gnome.org/Projects/GnomeShellIntegrationForChrome/Installation") for instructions about installing connector.
---
Any idea ?
Thanks

Precision - it doesn't work at all - Ubuntu on Xorg, Gnome Classic, Gnome, etc...

---

### Post by tea for one on 2021-10-15
I assume that you are using Firefox to organise your extensions?
Firefox in Ubuntu 21.10 is a snap package and does not currently allow you to install and manage gnome-extensions.

[https://www.omgubuntu.co.uk/2021/10/things-to-do-after-installing-ubuntu-21-10](https://www.omgubuntu.co.uk/2021/10/things-to-do-after-installing-ubuntu-21-10) - Item 6
[https://forum.snapcraft.io/t/firefox-snap-lacks-gnome-extension-integration/26792](https://forum.snapcraft.io/t/firefox-snap-lacks-gnome-extension-integration/26792)

As an experiment, I downloaded [COLOR="#0000FF"]Vivaldi[/COLOR], followed the instructions for integrating extensions and installed a few in 21.10.
Working OK so far with minimal testing.

---

### Post by Dennis N on 2021-10-15
Yes, Firefox Snap cannot manage extensions. Neither can Chromium Snap
_Alternatives_:
1 - Install the .deb version of Firefox. As far as I know, it's still in the Ubnutu repository. It can exist along with the Snap version. You can remove the Snap version if you want.
or 2 - Download and manually Install Mozilla's Firefox. 
or 3 - Install the extensions manually. It's not hard to do.

If you happen to have installed a development version (like the beta) before the release and upgraded to the release, then you already should have two Firefox. Only the Snap shows in the dock, so they hide the other one from you, but the overview search or application menu will reveal it.

---

### Post by grahammechanical on 2021-10-15
I can confirm that the deb version of Firefox is in the 21.10 repositories and can be installed. I have done it.

Regards

---

### Post by rudolf-kunzli on 2021-10-15
I removed the snap version of Firefox and installed the DEB version of it.
I could fix the problems with one gnome shell extension: replacing Topicon with TopiconFix.
Every thing runs fine now.
Thanks for you help - it is much appreciated !
Rudolf

Where do I close the thread ???

---

### Post by tea for one on 2021-10-15
You cannot close the thread without moderator intervention.

It is better to mark the thread as solved so that other users can benefit from the advice offered.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by rudolf-kunzli on 2021-10-15
Okay, I marked it solved...

---

