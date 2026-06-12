---
title: "Ubuntu 9.04 to Ubuntu 9.10 won't upgrade!"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by Logan513 on 2011-12-26
So, I've booted into Ubuntu 9.04 after not using it in quite a long while, and it prompted me with the familiar update manager. I clicked update to update to the latest version of Ubuntu and it said that the update from 9.04 to the latest build (whatever that is) is not supported by that tool. So I did some digging online, and found this:

[http://askubuntu.com/questions/47807/skipping-intermediate-ubuntu-os-upgrade-to-latest-one-how-do-i-upgrade-from-9-04](http://askubuntu.com/questions/47807/skipping-intermediate-ubuntu-os-upgrade-to-latest-one-how-do-i-upgrade-from-9-04)

From there, I downloaded the .iso, clicked no on downloading the most recent updates, and fallowed all the instructions only to get this:

[IMG]http://i.imgur.com/dHWp4.png[/IMG]

I'm all out of ideas, and at this point Google isn't being much of a help either. So you guys are my last hope. What do I do? All I want to do is update to Ubuntu 10.04 (No further, because I hate the interface on 11).

Thank you!
++LOGAN++

P.S. Also, I am running the 64bit version of Linux (yes, I did download the amd64.iso and got that error).

---

### Post by snowpine on 2011-12-26
Best to back up your documents and files, download a 10.04 CD, and do a fresh install. 

If you must do an "upgrade in place" then there are a few extra steps, since 9.04 and 9.10 are **both** "end of life."

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Logan513 on 2011-12-26
> **snowpine said:**
> Best to back up your documents and files, download a 10.04 CD, and do a fresh install. 

If you must do an "upgrade in place" then there are a few extra steps, since 9.04 and 9.10 are **both** "end of life."

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


Well, I wouldn't have any problems staying at the current version that I am at now... But I can't seem to get certain programs to install properly. I.E. qbittorrent (which I was trying to install earlier)

---

### Post by snowpine on 2011-12-26
> **Logan513 said:**
> Well, I wouldn't have any problems staying at the current version that I am at now... But I can't seem to get certain programs to install properly. I.E. qbittorrent (which I was trying to install earlier)

That's because 9.04 is "end of life" and no longer supported since Oct. 2010.

10.04 is the oldest version that's still supported (through April 2013).

---

### Post by West201 on 2011-12-26
Just curious, why do want to use the 9.10 version ?

---

### Post by fdrake on 2011-12-26
[http://www.qbittorrent.org/download.php](http://www.qbittorrent.org/download.php) the website let's you download the source code of the program so that you ken build you own binary. Also notice that your version should be supported in the repo check the repo list if it is still available.
> 
Ubuntu packages
Ubuntu

qBittorrent is now available in official Ubuntu repositories since v9.04 "Jaunty". Packages are automatically imported from Debian repositories are they are maintained on Ubuntu by Andrew Starr-Bochicchio.

More up-to-date Lucid/Maverick/Natty packages are published on my PPA here. To use this PPA please use the following command:
# qBittorrent Stable
sudo add-apt-repository ppa:hydr0g3n/ppa

# qBittorrent Unstable (For testing)
sudo add-apt-repository ppa:hydr0g3n/qbittorrent-unstable

Then install qBittorrent by doing this:
sudo apt-get update && sudo apt-get install qbittorrent


How is your internet connection. Can you try to upgrade online:
[http://www.linux-support.com/cms/en/component/content/article/4-howtos/136-online-upgrade-to-ubuntu-910-at-command-line?directory=14](http://www.linux-support.com/cms/en/component/content/article/4-howtos/136-online-upgrade-to-ubuntu-910-at-command-line?directory=14)

---

### Post by mörgæs on 2011-12-27
If you don't like the interface of Ubuntu past 10.04, you could also take a look at Xubuntu 11.10.

---

