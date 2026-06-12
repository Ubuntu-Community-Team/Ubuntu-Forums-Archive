---
title: "Offline Synaptic Package Manager"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by Sharkmeister on 2007-09-28
I am fairly new to Ubuntu and really love it but I have come across a problem that I can't find a solution to online.
Initially my Applications Menu stopped working and since I couldn't find a fix for that that worked, I asked a friend of mine and she suggested uninstalling gnome-menus and gnome-panel. I did that and uninstalled everything else that Synaptic Package Manager marked.

Now I can't boot unless I use the failsafe terminal session. I can get into Synaptic package manager that way using "sudo", but I can't connect to the internet (wireless network) to download and install the necessary programs.

Is there a way that I can write a CD with all the files on it so that I can do an offline installation?

---

### Post by jrib on 2007-09-28
There are a few ways.  If you just need the packages that got installed, you can use the Alternate CD (option on the ubuntu.com download page).  You can also use the Ubuntu DVD which has all of the main and restricted repositories on it.  You could also check out the "apt-zip" package and the [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) project.

The easiest way would probably be the alternate CD.  You can just pop that in your drive and it should prompt you to use it as a repository.  If not, use "apt-cdrom" on the command line.

On another ntoe, check out [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs) to see if you can get wifi going.

---

