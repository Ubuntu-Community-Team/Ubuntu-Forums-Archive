---
title: "Update from 9.04 to 9.10 from terminal?"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Faid on 2010-07-01
I'm running Ubuntu 9.04 as a VMWare image and I'd like to upgrade to 9.10. However, when I click on the Upgrade button in the Update Manager, a dialog pops up and says "Could not find the release notes. The server may be overloaded.". I doubt the server is overloaded though. 9.04->9.10 is still supported, even though 10.04 is out, right? Is it possible to upgrade from the terminal using sudo aptitude?
Updating applications and libraries from the Update Manager works fine, but despite this I'm suspecting that the network proxy configuration is somehow causing this. I've added the proxy address in System->Preferences->Network Proxy, in the Synaptic Package Manager, in .bashrc and .profile.

-F

---

### Post by combo123 on 2010-07-01
[http://www.thegeekstuff.com/2009/11/step-by-step-guide-to-upgrade-ubuntu-9-04-to-9-10-with-screenshots-%E2%80%93-jaunty-jackalope-to-karmic-koala/](http://www.thegeekstuff.com/2009/11/step-by-step-guide-to-upgrade-ubuntu-9-04-to-9-10-with-screenshots-%E2%80%93-jaunty-jackalope-to-karmic-koala/) 
I think this will work (this worked for me [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]). [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by dino99 on 2010-07-01
replace jaunty by karmic into the synaptic repo list, then update/upgrade

note that big changes have been made: grub2 replace grub-legacy, udev replace hal, xorg.conf not needed, ...)

---

