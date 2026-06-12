---
title: "Lubuntu 20.04 LTS Desktop - Intallation Failed - filesystem.squashfs"
date: 2020-07-14
forum: Installation &amp; Upgrades
---

### Post by stone.john on 2020-07-14
I'm an average Linux user.  Been using Lubuntu since 14.04... Now trying to install Lubuntu 20.04 LTS Desktop using VirtualBox 5.2.40r. (correct, this isnt 6 as it had some issues at the beginning when it came out).

I manage to get the installation running, however, midway though installation i get the following error:

[ATTACH=CONFIG]286465[/ATTACH]
 "Installation Failed
Failed to unpack image"/cdrom/casper/filesysm.squashfs
 rsync failed with error code 2"

I remember having similar issues in the past but that was on the machine where i just relugged the USB.  Here is the VM. 

I'm under the impression that 20.04 is stable/long term.  Is there a work around for this error?

---

### Post by stone.john on 2020-07-14
Turns out it was bad .iso.  After downloading again, everything went through well.

---

### Post by guiverc on 2020-07-14
Yes `squashfs` errors are related to media failures, either a bad write to your media (usually not applicable to VM installs but can still apply), or an invalid download (bad ISO).

I'll provide [https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)
though I generally trust my `zsync` download as it performs a checksum check post-download, and will report  failure.

---

### Post by ActionParsnip on 2020-07-15
If you use torrents then the data will be checked as it is downloaded. Always always check the ISO before using it. TCP is pretty good at catching bad packets but it isn't perfect.

---

