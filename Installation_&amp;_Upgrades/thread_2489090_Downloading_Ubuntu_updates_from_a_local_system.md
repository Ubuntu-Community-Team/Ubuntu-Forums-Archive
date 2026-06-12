---
title: "Downloading Ubuntu updates from a local system"
date: 2023-07-18
forum: Installation &amp; Upgrades
---

### Post by Hans_van_Leeuwen on 2023-07-18
In our company we have +/- 25 Ubuntu Linux systems in use.
When new updates become available, they are downloaded and installed on all that 25 Ubuntu systems.
In the current configuration, those updates are downloaded on all 25 Ubuntu systems from a remote server.
E.g. [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu)
This is configured in the file /etc/apt/sources.list
Of course, it is not practical to download a file containing an update 25 times from a remote system.
I want to set it up so that a file which contains the update, is downloaded once on a local update server.
Then the 25 Ubuntu systems can download the file, which contains the update, from that local update server.
However, I do not have space to set up a complete mirror of [http://nl.archive.ubuntu.com/ubunu](http://nl.archive.ubuntu.com/ubunu)

Can anyone give my directions how I can set up and configure this?

---

### Post by ActionParsnip on 2023-07-18
[https://kc.jetpatch.com/hc/en-us/articles/360052181591-Setting-Up-Local-Repositories-Ubuntu-](https://kc.jetpatch.com/hc/en-us/articles/360052181591-Setting-Up-Local-Repositories-Ubuntu-)
Setting up a LAN based repo is fantastic and saves bandwidth

You could copy the downloaded debs from one server that has updated to the rest, then run updates but it'll be very time consuming and doesn't scale. Simply pointing any new servers to an update server that accesses the web facing repos will be much faster. You can use the cheapest nastiest server for this or even a VM. Doesn't need much horsepower at all. A Raspberry Pi can do this if you have one laying around.

---

