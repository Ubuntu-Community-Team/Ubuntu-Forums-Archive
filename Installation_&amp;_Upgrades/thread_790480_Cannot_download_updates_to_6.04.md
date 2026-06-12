---
title: "Cannot download updates to 6.04"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by BroadwayLion on 2008-05-11
I had installed 6.04 to this computer two years ago, and it worked just fine. I had not used it in a while, since I was playing with a new Vista box. After some reorginization of our local network, I came back to this machine, and tried to upgrade it to 8.04, but it needed updates first. No problem, click on the icon, run the thing and WHAT! No Joy! It will not update any of my existing packages. It is as if it cannot even find the update site. Oh it knows I need 61 updates, and it even knows which ones I need, but it will not download them, let alone install them. The error messages say that the packages have been removed, or that the site has moved. I have tried this several times, but no joy on this project. OK, I download and burn a new .iso disk pop that in, and it opens the same upgrade window, but I have know idew what to sellect, or how to make it only look in the CD, it seems that it may have added the CD contents to what was already displayed. 

Does anybody have any suggestions as for what to do next?

Thanks, Elias

---

### Post by Pumalite on 2008-05-11
Post the output of:
sudo apt-get update

---

