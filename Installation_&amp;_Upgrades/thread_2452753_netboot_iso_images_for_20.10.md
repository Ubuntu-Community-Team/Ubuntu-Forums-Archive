---
title: "netboot iso images for 20.10"
date: 2020-10-27
forum: Installation &amp; Upgrades
---

### Post by mathiraj on 2020-10-27
The netboot iso images are missing for 20.10 release

For 20.04, the following location has the files
[http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/)

For 20.10 navigating to the location
[http://archive.ubuntu.com/ubuntu/dists/groovy/main/installer-amd64/current/legacy-images/](http://archive.ubuntu.com/ubuntu/dists/groovy/main/installer-amd64/current/legacy-images/)

don't have any netboot iso images. Would they be updated later or there won't be a 20.10 netboot install images?

---

### Post by DuckHook on 2020-10-27
I believe that Canonical has decided to discontinue netboot after Focal. I'll try to find the old thread and reference it.

---

### Post by DuckHook on 2020-10-27
My mistake. It will be shut down on 22.04. Here is the posting from Mörgæs referencing Canonical's decision: [https://ubuntuforums.org/showthread.php?t=2443643&p=13958386#post13958386](https://ubuntuforums.org/showthread.php?t=2443643&p=13958386#post13958386)

---

### Post by mathiraj on 2020-10-28
Thanks @DuckHook for the reply. So, does that mean the netboot mini.iso would be available for 20.10 after a few days?

---

### Post by DuckHook on 2020-10-28
> **mathiraj said:**
> …does that mean the netboot mini.iso would be available for 20.10 after a few days?

After reading the linked Discourse thread carefully, I note [here]("https://discourse.ubuntu.com/t/netbooting-the-live-server-installer/14510/61") that developer #Vorlon says:> We do still provide a mini.iso image for 20.04 at [http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso) 121 **but expect to drop this in the 20.10 cycle**.
I hadn't noticed that before (I just got tired of parsing through such a long thread). I guess this means that my original post was inadvertently accurate: there will be no mini.iso after 20.04.

This saddens me. I use the mini.iso for a number of scenarios. However, as per [that earlier thread]("https://ubuntuforums.org/showthread.php?t=2443643&p=13958393#post13958393"), Debian still offers and maintains [a mini.iso]("https://wiki.debian.org/DebianInstaller/Netboot") and since Ubuntu is Debian&#8209;based, it's not hard to learn a Debian OS.

If you do find a Groovy&#8209;based mini.iso, please post back on these forums, as there are more than a few of us who would welcome its resurrection. However, I wouldn't hold my breath.

---

