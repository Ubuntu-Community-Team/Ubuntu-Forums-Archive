---
title: "Update Manager warns but won't Update!"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by videodesigner on 2011-09-21
Ubuntu 11.04 

Update manager window displays this message:

 "Software updates may be available for your Computer. The package information was last updated 10 days ago. Press the 'Check' button below for new software updates." 

When the Check button completes, A dialog box displays the message:

  "Failed to download repository information.  Check your internet connection."

The details are:
 W:Failed to fetch [http://ppa.launchpad.net/rowinggolfer/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/rowinggolfer/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/rowinggolfer/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/rowinggolfer/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


I ran the following commands in the terminal window:

  [B]sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

[/B]The final messages were:

W:Failed to fetch [http://ppa.launchpad.net/rowinggolfer/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/rowinggolfer/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W:Failed to fetch [http://ppa.launchpad.net/rowinggolfer/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/rowinggolfer/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E:Some index files failed to download. They have been ignored, or old ones used instead.


Is this something I should be concerned about, or can I ignore it.   The rest of the software seems to be current.

---

### Post by plucky on 2011-09-21
Just remove that PPA from your Software Sources.

There isn't a PPA for Natty, See [Here](http://ppa.launchpad.net/rowinggolfer/ppa/ubuntu/dists/)

Good Luck

---

### Post by videodesigner on 2011-09-21
Thanks Plucky,  that resolved the issue.

---

