---
title: "Can't find repository after installation"
date: 2017-05-03
forum: MINT
---

### Post by erikoma on 2017-05-03
I may seem like a new user but I've been using Ubuntu for 10 years. Just couldn't find my old account.

After installation and first boot of Ubuntu server, the repository is not found and no further installations or updates can be made. This is valid for version 16.04 LTS as well as for 16.10 and 17.04 The last version I installed from scratch was probably before any of these, and have not seen this problem before. 
I suspected the computer but the same happens on another computer (same brand but different motherboard/CPU).
I'm now using a temporary work-around by using Linux Mint on the server, based on Ubuntu 16.10, but naturally I have no use for a graphic desktop on the server.
The repository it's looking for is no.archive.ubuntu.com . This repository seems to be non-existing.
Has anyone else experienced this? Any solution?

---

### Post by howefield on 2017-05-03
Thread moved to the "*MINT*" forum.

---

### Post by Dennis N on 2017-05-03
no.archive.ubuntu.com is one of the 441 mirrors for the ubuntu archive:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

It's found under Norway. Could be temporarily down? You could change to another mirror and try again. 

Settings > Software and Updates > Ubuntu Software > Download From:

---

### Post by erikoma on 2017-05-03
Before rebooting the mirror works just fine.

---

