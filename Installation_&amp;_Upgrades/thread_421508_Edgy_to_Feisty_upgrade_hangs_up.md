---
title: "Edgy to Feisty upgrade hangs up"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by kealan on 2007-04-24
I'm using update-manager to upgrade to 7.04.  I get to the "Preparing the upgrade" stage and it hangs up while Fetching file 370 of 387.  I have tried several times and it always hangs up on this file.  Any suggestions?

---

### Post by ciscosurfer on 2007-04-24
> **kealan said:**
> I'm using update-manager to upgrade to 7.04.  I get to the "Preparing the upgrade" stage and it hangs up while Fetching file 370 of 387.  I have tried several times and it always hangs up on this file.  Any suggestions?If you know the name of the file, you can go to packages.ubuntu.com and download it manually.

---

### Post by marx2k on 2007-04-24
I had this same issue and I *think* it's one of your 3rd party repositories timing out or being unable to connect.

I removed all 3rd party repositories and it turned out great. Try that.

---

### Post by kealan on 2007-04-24
> **marx2k said:**
> I had this same issue and I *think* it's one of your 3rd party repositories timing out or being unable to connect.

I removed all 3rd party repositories and it turned out great. Try that.

Well, that got things a little further along, now I'm getting 
**Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz) Sub-process gzip returned an error code (1)**

---

