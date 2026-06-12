---
title: "upgrade problem"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by skrizwanali on 2011-09-29
whenever i update ubuntu 11.04 using update manager it prompts 'download failed check your internet connection' after sometimes of checking up the update release...why this happens?..and what is the solution?
again when i use the command 'sudo apt-get update && sudo apt-get upgrade' in the terminal it shows :
"Fetched 2,324 B in 5min 11s (7 B/s)
W: Failed to fetch [http://ppa.launchpad.net/linux-3.0/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/linux-3.0/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/linux-3.0/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/linux-3.0/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release](http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release)  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead."
what should i do????????
PLZ HELP

---

### Post by plucky on 2011-09-30
> **skrizwanali said:**
> whenever i update ubuntu 11.04 using update manager it prompts 'download failed check your internet connection' after sometimes of checking up the update release...why this happens?..and what is the solution?
again when i use the command 'sudo apt-get update && sudo apt-get upgrade' in the terminal it shows :
"Fetched 2,324 B in 5min 11s (7 B/s)
W: Failed to fetch [http://ppa.launchpad.net/linux-3.0/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/linux-3.0/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/linux-3.0/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/linux-3.0/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release](http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release)  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead."
what should i do????????
PLZ HELP

Open your Software Sources and disable the PPA for linux-3.0 as it doesn't exist on Launchpad.

The team-xbmc PPA doesn't have a repository for Natty (See [Here](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/)) so disable or delete it.

Also remove the virtualbox repository as it is for Maverick.

Good Luck

---

### Post by plucky on 2011-09-30
Please keep any questions on the forum.

From 2 private messages:-

[QUOTE=skrizwanali]can u plz tell me that in more details????what is ppa?[/QUOTE]

> when i use the commnd youtube-dl it dosent work anymore shows error..initially it was working gr8..why is it so can u tell me plz???how can i install linux 3.0 kernal??????can i get xmbc for natty?

---

### Post by skrizwanali on 2011-10-11
thnx for the help it really worked

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

[http://www.upubuntu.com/2011/07/remo...e-404-not.html](http://www.upubuntu.com/2011/07/remo...e-404-not.html)

---

