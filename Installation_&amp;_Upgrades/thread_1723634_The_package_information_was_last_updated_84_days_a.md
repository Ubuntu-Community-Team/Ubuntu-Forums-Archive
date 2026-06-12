---
title: "The package information was last updated 84 days ago?"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2011-04-07
> The package information is up to date.

The package information was last updated 84 days ago.Should this concern me, and how do I remedy it? Some updates do install regularly, but I do not understand what 84 day old package information Update Manager is referencing.

When in Update Manager I try to check for new updates it tells me:

> Failed to download repository information

Check your Internet connection.

W:Failed to fetch [http://ppa.launchpad.net/zentyal/2.0/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/zentyal/2.0/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.If upon reading this you know the solution, please make me aware of it and any complete commands I need to enter into terminal if necessary.

---

### Post by mörgæs on 2011-04-07
Try booting the machine and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Dáire Fagan on 2011-04-07
> **mörgæs said:**
> Try booting the machine and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

I rebooted and logged into X/Gnome, you didn't mean bring up a terminal before logging into X, right? If you did please tell me what the key is to do so.

> dusf@skyrocket:~$ sudo apt-get clean
dusf@skyrocket:~$ sudo apt-get update

....

Fetched 4,911B in 2s (2,370B/s)
W: Failed to fetch [http://ppa.launchpad.net/zentyal/2.0/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/zentyal/2.0/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
E: Some index files failed to download, they have been ignored, or old ones used instead.

dusf@skyrocket:~$ sudo apt-get updgrade

...

Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by plucky on 2011-04-07
> W: Failed to fetch [http://ppa.launchpad.net/zentyal/2.0...86/Packages.gz](http://ppa.launchpad.net/zentyal/2.0...86/Packages.gz) 404 Not Found
W: Failed to fetch [http://ppa.launchpad.net/nvidia-vdpa...86/Packages.gz](http://ppa.launchpad.net/nvidia-vdpa...86/Packages.gz) 404 Not Found
E: Some index files failed to download, they have been ignored, or old ones used instead.

Those PPAs do not have a repository for Maverick

See [Here](http://ppa.launchpad.net/zentyal/2.0/ubuntu/dists/)
and [Here](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/)

so remove them from your sources.list.

Or they might be located in /etc/apt/sources.list.d/ directory.

Open Software Sources and un-tick them as a source.

Good Luck

---

### Post by Dáire Fagan on 2011-04-07
> **plucky said:**
> Those PPAs do not have a repository for Maverick

See [Here]("http://ppa.launchpad.net/zentyal/2.0/ubuntu/dists/")
and [Here]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/")

so remove them from your sources.list.

Or they might be located in /etc/apt/sources.list.d/ directory.

Open Software Sources and un-tick them as a source.

Good Luck

Perfect, many thanks!

---

### Post by mörgæs on 2011-04-07
Good, please mark the thread 'solved'.

---

### Post by Dáire Fagan on 2011-04-07
> **mörgæs said:**
> Good, please mark the thread 'solved'.

My bad, actually looked for that option earlier but must have missed it.

---

