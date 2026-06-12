---
title: "smcFanControl - PPA update error"
date: 2015-07-04
forum: MINT
---

### Post by Justin832 on 2015-07-04
I am running Linux Mint 17.1 Xfce on a MacBook Pro.  The laptop was getting very hot, so I installed smcFanControl (ref: [http://ubuntuforums.org/showthread.php?t=1754431](http://ubuntuforums.org/showthread.php?t=1754431)).  The computer runs much cooler now, but apparently I should not have executed step 10:
sudo add-apt-repository ppa:alexeftimie/ppa
sudo apt-get update
sudo apt-get install indicator-sysmonitor

I was able to add the repository, but the indicator-sysmonitor did not install.  Now I see these errors in my Update Manager:
W:Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/source/Sources) 404 Not Found
W:Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages) 404 Not Found
W:Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/binary-i386/Packages) 404 Not Found
E:Some index files failed to download.  They have been ignored, or old ones used instead.

I tried to remove the PPA using the following (all to no avail):
sudo ppa-purge ppa:alexeftimie/ppa
sudo apt-add-repository --remove ppa:alexeftimie/ppa
sudo apt-add-repository remove ppa:alexeftimie/ppa
sudo add-apt-repository --remove ppa:alexeftimie/ppa
sudo add-apt-repository remove ppa:alexeftimie/ppa
apt purge ppa:alexeftimie/ppa

The terminal response was either "--remove is not an option", or a new command line.  

The ppa-purge command gave me this:
"
W:Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/source/Sources) 404 Not Found

W:Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages) 404 Not Found

W:Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/trusty/main/binary-i386/Packages) 404 Not Found

E:Some index files failed to download.  They have been ignored, or old ones used instead.
Warning: apt-get update failed for some reason
PPA to be removed: alexeftimie ppa
Warning: Could not find package list for PPA: alexeftimie ppa
"

So how do I remove these errors from my update manager?  
Ideally, I'd like to remove everything I added when I ran: "sudo add-apt-repository ppa:alexeftimie/ppa", but I would like to keep smcFanControl.

---

### Post by howefield on 2015-07-04
Thread moved to the "*MINT*" forum.

---

### Post by Justin832 on 2015-07-04
Digging further, it looks like I could disable the PPA or "remove permanently" using "Software Sources".  Is this a bad idea?

---

### Post by Rob Sayer on 2015-07-06
No, it'd be a very good idea to remove that ppa.

None of the stuff you get from those ppa's has been beta tested.  Beta tested software from the repos is one of the nicest features of linux.  I won't use ppa's for app software unless the app does something I can't do without and is not in the repos.  For lower level stuff like that?  Not a hope in hell.

I haven't used anything like that app but I suspect there are better ways to deal with your power management issues.

---

