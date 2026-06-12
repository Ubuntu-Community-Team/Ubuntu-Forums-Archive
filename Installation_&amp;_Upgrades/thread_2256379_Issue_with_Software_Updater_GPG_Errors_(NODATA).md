---
title: "Issue with Software Updater GPG Errors (NODATA)"
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by dean-westray on 2014-12-11
I am having trouble with the Software Updater over the last two days.  I am getting "Failed to download respository information" errors when I run the Software Updater.   On running "sudo apt-get update", I am getting the following message in the terminal.

100% [Waiting for headers] [3 InRelease gpgv 2,899 B] [Connecting to dl.google.Splitting up /var/lib/apt/lists/partial/ppa.launchpad.net_berfenger_roccat_ubuntuIgn [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
E: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)


On further testing I have had GPG errors on several of the other main Utopic GB respositories, as well as some of the few PPAs I use.   Is there an ongoing issue with the GB Utopic servers at this current time?   Both my PC and laptop are running 14.10, and running into the same problem.

---

### Post by papibe on 2014-12-11
Hi dean-westray.

Are you using mobile broadband? If so, take a look at this: [Faulty proxy on mobile broadband]("http://askubuntu.com/questions/474549/got-nodata-issue-nodata-does-the-network-require-authentication").

Let us know how it goes.
Regards.

---

### Post by dean-westray on 2014-12-12
Thanks for pointing me in right direction.   I'm not using mobile broadband ISP, (I'm on Plusnet here in the UK).   I have checked with Plusnet this afternoon (as per the page) re: transparent proxies.  They confirmed they don't have any transparent proxies running on the connection.   I've double checked with my own network here and I have no proxies set up on my router or my other machines.  

Would the GB Ubuntu servers be running behind a proxy?  Any further input please, would be greatly appreciated.

---

