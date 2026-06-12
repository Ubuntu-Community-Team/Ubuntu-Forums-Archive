---
title: "need help in canceling the installation of ubuntu-restricted-extras"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by fundamentalabd on 2010-07-27
i know it that i need to install ubuntu-restricted-extras package in order to play some audio or video files in default ubuntu (using rhytmbox or totem). i connect to the internet from my college. i install many packages by using apt in terminal and download them from a local repositories. i put this command to terminal 'sudo apt-get install ubuntu-restricted-extras' and it worked as usual (downloading package and installing in normal way). but i got problem when it had to download the restricted which had to be downloaded from the their web directly (from sourceforge.net) which i couldn't even connect to it (i can normally browse any web from firefox but my ubuntu even cannot download and install any package from the main ubuntu repositories). so i decided to cancel the installation by simply forced the terminal to quit. but when i tried to install another packages using the same way, it said 
"E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
"
may be the dpkg is still used by the installation of that package. how can i cancel it?

---

### Post by Frogs Hair on 2010-07-27
See If the packages started to install . go to synaptic package manager and search for Ubuntu Restricted Extras. Remove the unwanted packages by right clicking and marking for removal (Select Apply). Next go to the home folder and press ctlr+h on the keyboard to show hidden folders and look for and remove the folder.

---

### Post by fundamentalabd on 2010-07-28
some packages of ubuntu-restricted-extras were installed succesfully but some cannot be downloaded so i just closed the connection and let the installer tried to download for several times and it ended and failed. i can play what i want now. thanks

---

