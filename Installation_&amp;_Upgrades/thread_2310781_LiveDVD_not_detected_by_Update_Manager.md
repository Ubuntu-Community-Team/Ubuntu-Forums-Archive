---
title: "LiveDVD not detected by Update Manager"
date: 2016-01-21
forum: Installation &amp; Upgrades
---

### Post by anotherChris on 2016-01-21
I'm running Lubuntu 11.10, which was installed by a friend.  I want to upgrade to 15.10 and have gotten to the point of creating a LiveDVD.  I've done the check sums and also checked the DVD for errors.  Everything is okay, and the LiveDVD boots on my laptop.  

There is a problem with my wi-fi, however, so I will have to install new drivers.  I think this might be beyond me because I am basically new to Ubuntu, I am in a foreign, non-English-speaking country, and I only have wi-fi, so I will lose Internet access if I install from the 15.10 LiveDVD.

I had the idea that if I upgraded rather than fresh installing, my current wi-fi driver might be preserved.  However, when I go into the 11.10 Update Manager (where there is an option "Installable from CD-ROM/DVD" under the heading "Software Sources") and put in my 15.10 LiveDVD, the Update Manager does not detect anything to install.  (I also get an error message when trying to use Internet sources.)

Is this the expected situation?  If not, can I get the Update Manager to detect the LiveDVD?

---

### Post by Frogs Hair on 2016-01-22
Hello 

There is no direct upgrade path from 11.10 to 15.10 . Upgrades have to be done in order to the next released version with the exception of long term support releases. 12.04 LTS is the next version and still supported. I would suggest a file backup and clean installation of either 14.04 LTS or 15.10. Either of these would allow for an upgrade to 16.04 LTS coming in April.

---

### Post by grahammechanical on 2016-01-22
> (I also get an error message when trying to use Internet sources.)

That is because the repositories for Ubuntu 11.10 are closed and have been moved from the servers that they were on. So, the URLs in the software sources list are incorrect.

Each version of Ubuntu has its own set of repositories which are closed when the version reaches end of life. Before upgrading to the next release the present installed version of Ubuntu needs to be updated. Which is now difficult for Ubuntu 11.10 to do as the repositories are now closed.

If you some how managed to use the live DVD to upgrade 11.10 to 15.10 you might find that you have a broken OS. You might also find that the upgrade does not actually upgrade but over-writes what is on the drive. Are you prepared to loose all your data?

Have you tried making a WiFi connection with the live session of 15.10? You might find that there is a driver in 15.10 for that wireless adapter that did not exist when 11.10 was released.

You might want to try this to make the jump from 11.10 to 12.04

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

After changing the URLs to old-releases.ubuntu.com remember to update the OS and also to revert to using an open source video driver before upgrading.

Regards

---

### Post by anotherChris on 2016-01-25
I'm on 15.10 now.  Thanks!

---

