---
title: "Problem Installing Updates"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by dogdog on 2008-06-05
I am using Hardy Heron 8.04 LTS (upgraded from v 7.10 at end April).

I have had problems installing Updates. Update Manager got stuck but I had partial success with Synaptic Package Manager.With Synaptic I have managed to install 77 out of 103 updates.

When I tried to install emaining 26 updates I got message:

An error occurred. The following details are provided.

Then 26 messages (one for each failed update)along the following lines:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/...2.22.1-Oubuntu](http://gb.archive.ubuntu.com/ubuntu/...2.22.1-Oubuntu) 2.1_i386.deb 404 Not Found (IP: 91.189.88.45 80)

Is this a temporary problem with ubuntu server or symptomatic of a problem at my end??

Synaptic said no broken packages.

Any reason why the updates that did work, worked with Synaptic Package Manager but not with Update Manager??

Again - many thanks for help.

---

### Post by PmDematagoda on 2008-06-05
Refresh your sources list with:-
```
sudo apt-get update
```
and then try installing the updates with:-
```
sudo apt-get upgrade
```

---

### Post by dogdog on 2008-06-05
That worked.

Thanks alot.:)

---

