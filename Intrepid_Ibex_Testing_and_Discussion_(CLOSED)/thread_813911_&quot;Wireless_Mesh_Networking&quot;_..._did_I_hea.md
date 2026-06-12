---
title: "&quot;Wireless Mesh Networking&quot; ... did I hear that right?"
date: 2008-05-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by diablo75 on 2008-05-31
I was watching a video in the Ubuntu Developers Youtube channel (I don't remember which video) and a question was about to be raised about wireless mesh networking, but was forgotten/replaced by another question.  So nothing was said about the topic.

So I'm just shooting a little curiosity out there:  Are there plans to push out support for 802.11s networking?

---

### Post by gnomeuser on 2008-05-31
.11s is only a draft currently as I recall, but we have mesh networking working on the OLPC hardware. It should be possible, the problem is getting vendors to open their specs for the new chipsets. We already have a problem supporting .11n networks because of this. 

So please if you want this, vote with your dollars and buy from a vendor that will support Free Software by working with us.

---

### Post by plun on 2008-05-31
> **diablo75 said:**
> 
So I'm just shooting a little curiosity out there:  Are there plans to push out support for 802.11s networking?

MarkS wrote this about Intrepid

> A particular focus for us will be pervasive internet access, the
ability to tap into bandwidth whenever and wherever you happen to
be. No longer will you need to be a tethered, domesticated animal -
you'll be able to roam (and goats do roam!) the wild lands and
access the web through a variety of wireless technologies. We want
you to be able to move from the office, to the train, and home,
staying connected all the way.

[https://lists.ubuntu.com/archives/ubuntu-devel/2008-February/025136.html](https://lists.ubuntu.com/archives/ubuntu-devel/2008-February/025136.html)



Open or proprietary stuff should just work....  everything that
a main stream user buys must work and this must be the goal for intrepid.

The NetworkManager is just a joke for the moment....  just take a look within the wireless forum....

---

### Post by gnomeuser on 2008-05-31
> **plun said:**
> 
The NetworkManager is just a joke for the moment....  just take a look within the wireless forum....

You mistake Network Manager with the wifi stack and drivers. 99% of all problems with NM are found in the drivers, they are young and often developed based on guess work and reverse engineering.

---

### Post by ronacc on 2008-05-31
then why did I have to kill NM to get my WIRED networking to connect the other day ? this has never happened before with any of the DOZENS of distros that have been on that box. I well understand the problems facing the devs with wireless but to screw up a common well supported wired network card takes real talent .

---

### Post by gnomeuser on 2008-06-01
> **ronacc said:**
> then why did I have to kill NM to get my WIRED networking to connect the other day ? this has never happened before with any of the DOZENS of distros that have been on that box. I well understand the problems facing the devs with wireless but to screw up a common well supported wired network card takes real talent .

could be a module loading problem as well (same has happened to me when a module experiences problems but won't let itself be forcefully removed), but that might very well also be a genuine NM problem, it's not perfect but the level of blame it faces is simply not related to reality.. which was the point.

People blame what they see as the point of failure, NM is the visible spearhead of the larger networking and wifi stack. It is maybe 1% of the total code needed to get networking running. Yet it is blamed for 100% of failures by a certain group who refuses to look into the specific issue.

---

### Post by ronacc on 2008-06-01
I did not dig in to the actual root cause of the problem , I simply "corrected " it in the quickest manner . The problem went away with the next series of updates so I suspect you are probably right . However the main point of the post was that it is possible to automaticly blame the app as eaisly as it is to automaticly blame propriatary drivers or hardware .

---

### Post by gradedcheese on 2008-06-01
We have a working implementation of draft-802.11s for the Linux kernel's mac80211 stack right here: [http://o11s.org]("http://o11s.org"), it has been merged into [compat-wireless]("http://linuxwireless.org/en/users/Download") for some time now and will probably be available in 2.6.26's mac80211.  

You can use this right now with the Zydas USB WiFi dongles (zd1211rw driver from compat-wireless) and there is a patch for the b43 driver.  open80211s sits in the mac80211 layer so it should be able to support almost any 'soft MAC' WiFi device, however it requires some minor changes to the underlying drivers (beaconing, etc).  If you have suitable hardware, please give it a try.

---

### Post by gradedcheese on 2008-06-04
Merged into 2.6.26, so coming soon to a kernel near you: [http://linux-foundation.org/weblogs/lwf/2008/05/05/the-shape-of-2626/](http://linux-foundation.org/weblogs/lwf/2008/05/05/the-shape-of-2626/) (second item mentioned) ...presumably that will be included in 8.10 along with the patched b43 and zd1211rw drivers.

---

