---
title: "Update problems occuring after installing Dropbox"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by saikatbib on 2012-08-30
Hi Everyone,
Few days ago I installed Dropbox in my Ubuntu 12.04 (64bit) desktop. At the time of installation there occurred some problems and I could not installed it properly in my computer. So that I removed it from my Desktop. After few days, I got a weired notification in the Upper panel of Desktop with "Red Sign" and it's saying that some applications failed to update properly. As a suggestion it's saying that to click the "check for updates " and update manually. I did it, but it was saying that some packages failed to update. I checked in the detail portion and found that some ```
W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/precise/main/source/Sources  Got a single header line over 360 chars

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/precise/main/binary-amd64/Packages  Got a single header line over 360 chars

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/precise/main/binary-i386/Packages  Got a single header line over 360 chars

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/precise/main/i18n/Translation-en_US  Got a single header line over 360 chars

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/precise/main/i18n/Translation-en  Got a single header line over 360 chars

E: Some index files failed to download. They have been ignored, or old ones used instead.
```It's looking that some Dropbox file still remained in my computer. Can anybody tell me how do I completely remove the Dropbox files, so that the update problem will solve?

---

### Post by togo59 on 2012-10-19
You probably have references to Dropbox in /etc/apt/sources.list

The upgrade tool uses this to determine what to download.

---

