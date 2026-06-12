---
title: "NetworkManager 0.7.1 in Jaunty?"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MadsRH on 2009-02-20
Since we're now past feature freeze and there might not be enough time for testing, perhaps this is a stupid question, but it seems there's a whole slew of fixes, updated translations, and new support in the NetworkManager 0.7.1. Is there any chance that this will make it into Jaunty? I don't know the release schedule for NetworkManager, but it is currently only Release Candidate 1.

One of the notable items in this release is NetworkManager now supports Internet connections provided over Bluetooth via GPRS devices. There are also various D-Bus changes and other items worth noting.

If not, I guess that's [one more for Jaunty+1]("http://anotherubuntu.blogspot.com/2009/02/what-you-wont-get-in-jaunty.html") ;-)

---

### Post by Nullack on 2009-02-20
nullack@PPP:~$ sudo apt-cache policy network-manager
[sudo] password for nullack: 
network-manager:
  Installed: 0.7.1~rc1-0ubuntu2
  Candidate: 0.7.1~rc1-0ubuntu2
  Version table:
 *** 0.7.1~rc1-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
        100 /var/lib/dpkg/status
nullack@PPP:~$

---

### Post by oldmanuk on 2009-02-20
excellent

---

### Post by olskar on 2009-02-20
> **MadsRH said:**
> Now supports Internet connections provided over Bluetooth via GPRS devices

That does not work with 0.7.1~rc1-0ubuntu2 in Jaunty..

---

### Post by andrewsomething on 2009-02-20
I can't seem to find the post, but I recall reading on the ubuntu-devel mailing list that the upstream 0.7.1 release will be before Jaunty. That's why 0.7.1~rc1 was pushed in before feature freeze. I'm almost certain the plan is still to include it.

---

